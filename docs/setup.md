# 🛠️ Guia de Início Rápido

Este template foi desenvolvido para facilitar a criação de materiais didáticos modernos e automatizados para a UNA. Siga os passos abaixo para configurar seu ambiente.

---

## 1. Configuração Local

Para editar e visualizar o site em sua máquina:

1. **Clone o repositório:**

```bash
git clone https://github.com/SEU_USUARIO/SEU_REPOSITORIO.git
cd SEU_REPOSITORIO

```

2. **Crie e ative o ambiente virtual:**

```bash
python -m venv venv
# No Windows:
.\venv\Scripts\activate
# No Linux/Mac:
source venv/bin/activate

```

3. **Instale as dependências:**

```bash
pip install -r requirements.txt

```

4. **Inicie o servidor de visualização:**

```bash
mkdocs serve

```

Acesse `http://127.0.0.1:8000` no seu navegador.

---

## 🚀 Publicação Automática (GitHub Pages)

O deploy está configurado via **GitHub Actions**. Para que funcione corretamente em seu próprio repositório:

!!! danger "Passo essencial: fonte do Pages"
    Em **Settings > Pages**, no campo **Build and deployment > Source**, selecione **"GitHub Actions"** — **não** deixe em *"Deploy from a branch"*. É a causa mais comum do erro `Deployment failed, try again later`.

1. Vá em **Settings > Pages > Build and deployment > Source** e escolha **"GitHub Actions"**.
2. Vá em **Settings > Actions > General**; em **Workflow permissions**, selecione **"Read and write permissions"** e salve.
3. Faça um `git push` para a branch **`main`**: o site é construído e publicado automaticamente. Pushes na `develop` apenas validam o build (não publicam).

!!! question "Deu `Deployment failed, try again later`?"
    Quase sempre a fonte do Pages ainda está em *"Deploy from a branch"* — volte ao passo 1. Depois de corrigir, use **Actions > (workflow) > Re-run jobs** ou faça um novo push na `main`. O aviso sobre *Node 20* que aparece no log é apenas informativo e **não** é a causa.

---

## 🎨 Personalização

* **Nome da Disciplina:** Altere o campo `site_name` no arquivo `mkdocs.yml`.
* **Menu Lateral:** Organize suas aulas e pastas na seção `nav:` do `mkdocs.yml`.
* **Cores e Temas:** Você pode alterar a cor primária de `indigo` para outras cores (ex: `red`, `blue`, `deep-purple`) no `mkdocs.yml`.

---

### 💡 Dica para o Professor

Para criar caixas de destaque (Admonitions), utilize a sintaxe abaixo nos seus arquivos Markdown:

```markdown
!!! tip "Dica"
    Seu conteúdo aqui com recuo de 4 espaços.

!!! info "Importante"
    Este template já conta com suporte a modo escuro automático!

```