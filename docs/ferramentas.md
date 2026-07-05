# 🧰 Instalação das Ferramentas

Antes de começar as atividades práticas, instale as ferramentas abaixo. Siga a ordem sugerida e, ao final de cada uma, use o comando de verificação para confirmar que a instalação deu certo.

!!! tip "Dica"
    Após instalar cada ferramenta, **feche e reabra o terminal** (ou o VS Code) para que os comandos passem a ser reconhecidos.

---

## 1. SDK .NET 10

Kit de desenvolvimento para criar e executar aplicações em C#/.NET.

- 🔗 **Download:** [dotnet.microsoft.com/pt-br/download/dotnet/10.0](https://dotnet.microsoft.com/pt-br/download/dotnet/10.0)

1. Baixe o instalador do **SDK** (não apenas o *Runtime*) para o seu sistema.
2. Execute o instalador e conclua com as opções padrão.
3. Verifique no terminal:

```bash
dotnet --version
```

---

## 2. OpenJDK 25

Ambiente de desenvolvimento Java (distribuição da Microsoft).

- 🔗 **Download:** [learn.microsoft.com/en-us/java/openjdk/download](https://learn.microsoft.com/en-us/java/openjdk/download)

1. Baixe o pacote da versão **25** para o seu sistema (`.msi` no Windows, `.pkg` no macOS, `.tar.gz`/pacote no Linux).
2. Instale com as opções padrão. No Windows, mantenha marcada a opção de adicionar o Java ao `PATH`.
3. Verifique no terminal:

```bash
java -version
```

---

## 3. Visual Studio Code

Editor de código que usaremos nas aulas.

- 🔗 **Download:** [code.visualstudio.com/download](https://code.visualstudio.com/download)

1. Baixe a versão para o seu sistema operacional e instale.
2. No Windows, marque **"Adicionar ao PATH"** durante a instalação.
3. Extensões recomendadas (instale pela aba *Extensions*, `Ctrl+Shift+X`):
    - **C# Dev Kit** (para .NET)
    - **Extension Pack for Java** (para Java)

---

## 4. Git

Controle de versão, usado para versionar o código e publicar os projetos.

- 🔗 **Download:** [git-scm.com/downloads](https://git-scm.com/downloads)

1. Baixe e instale para o seu sistema (no Windows, aceite as opções padrão).
2. Verifique no terminal:

```bash
git --version
```

3. Configure seu nome e e-mail (uma única vez):

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

---

## 5. Postman

Ferramenta para testar APIs (requisições HTTP).

- 🔗 **Download:** [postman.com/downloads](https://www.postman.com/downloads/)

1. Baixe e instale a versão para o seu sistema.
2. Abra o Postman. É possível usar sem criar conta clicando em **"Skip and go to the app"** / **"Continue without an account"**.

---

!!! success "Tudo pronto?"
    Se os comandos `dotnet --version`, `java -version` e `git --version` responderam com um número de versão, seu ambiente está configurado. Em caso de erro, confira se você reabriu o terminal após a instalação.
