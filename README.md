# Una - UC MkDocs Template

Template padrão para documentação de Unidades Curriculares (UC) utilizando **MkDocs Material**, com deploy automático no GitHub Pages.

## 🚀 Como usar este template

1. Clique em **"Use this template"** no topo deste repositório para criar o seu.
2. Clone o seu novo repositório e entre na pasta:
   ```bash
   git clone https://github.com/SEU_USUARIO/SEU_REPOSITORIO.git
   cd SEU_REPOSITORIO
   ```
3. Crie e ative o ambiente virtual:
   ```bash
   python -m venv venv
   # Windows
   .\venv\Scripts\activate
   # Linux/Mac
   source venv/bin/activate
   ```
4. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```
5. Inicie o servidor local:
   ```bash
   mkdocs serve
   ```
   Acesse `http://127.0.0.1:8000` no navegador.

## 🛠️ Tecnologias inclusas

- **MkDocs Material** — tema, navegação e modo escuro automático.
- **Plugin de Busca** (search) — busca integrada no site.
- **Git Revision Date** — data da última atualização em cada página.

## 📖 Publicação

O deploy no GitHub Pages é automático via GitHub Actions a cada `push` nas branches `main` ou `develop`. Consulte o **[Guia do Professor](docs/setup.md)** para o passo a passo de configuração e personalização.
