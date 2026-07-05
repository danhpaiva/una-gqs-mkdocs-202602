# Lista 02 — CI/CD e DevOps

!!! abstract "🎯 Missão"
    Criar um projeto Java simples e configurar um **pipeline de CI** no GitHub
    Actions que rode o build (e, se possível, os testes) a cada `push`.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** chamado **`una-gqs-lista02`**.
2. **Clone** e entre na pasta:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista02.git
    cd una-gqs-lista02
    ```
3. Adicione um pequeno programa Java e o workflow em `.github/workflows/ci.yml`.
4. **Suba** e confira a aba **Actions** ficando verde:
    ```bash
    git add .
    git commit -m "ci: adiciona pipeline de build no GitHub Actions"
    git push origin main
    ```
5. **Entregue o link** do repositório no **Google Classroom** (com o print do
    workflow verde no README).

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista02/
├── README.md
├── .github/
│   └── workflows/
│       └── ci.yml
└── src/
    └── App.java
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Pipeline que compila"
    Crie um `ci.yml` que faça checkout, configure o JDK e **compile** seu programa
    Java a cada push. Confirme que o job fica verde na aba Actions.

    ```yaml
    name: ci
    on: [push]
    jobs:
      build:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v4
          - uses: actions/setup-java@v4
            with:
              distribution: temurin
              java-version: '21'
          - run: javac src/App.java
    ```

??? abstract "Exercício 2 — Os três contínuos"
    No `README`, explique com suas palavras a diferença entre **Integração
    Contínua**, **Entrega Contínua** e **Implantação Contínua**. Dê um exemplo de
    sistema em que você **não** faria implantação automática.

??? abstract "Exercício 3 — Quebre de propósito"
    Introduza um erro de compilação, faça push e observe o pipeline **falhar**.
    Print o resultado, corrija e mostre o pipeline verde de novo. Documente no
    `README` o que aconteceu.

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** `una-gqs-lista02`.
    - [ ] Arquivo `.github/workflows/ci.yml` presente e válido.
    - [ ] Pipeline **verde** na aba Actions (com print no README).
    - [ ] Evidência do pipeline **falhando e voltando a passar** (Exercício 3).
    - [ ] Link entregue no **Google Classroom** antes do prazo.
