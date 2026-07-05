# Lista 01 — Qualidade e Garantia da Qualidade (QA)

!!! abstract "🎯 Missão"
    Consolidar os conceitos de qualidade de software (produto × processo) e a
    tríade **defeito / erro / falha**, produzindo um pequeno material analítico e
    versionado no GitHub.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** no GitHub chamado **`una-gqs-lista01`**.
2. **Clone** o repositório na sua máquina:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista01.git
    cd una-gqs-lista01
    ```
3. Resolva os exercícios (código em **Java** e respostas em Markdown).
4. **Suba o código** com commits pequenos e descritivos:
    ```bash
    git add .
    git commit -m "feat: resolve exercicios da lista 01"
    git push origin main
    ```
5. **Entregue o link** do repositório no **Google Classroom**.

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista01/
├── README.md          # identificação e índice das respostas
├── respostas/
│   ├── ex01.md        # classificação defeito/erro/falha
│   ├── ex02.md        # produto x processo
│   └── ex03.md        # shift-left
└── src/
    └── ClassificadorTermos.java
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Defeito, erro ou falha"
    Para cada situação, classifique e justifique:

    1. `if (idade > 18)` quando o requisito é "18 ou mais".
    2. A variável `total` fica com `-5` em memória durante a execução.
    3. O caixa libera saque acima do saldo para o cliente.

    Entregue em `respostas/ex01.md`.

??? abstract "Exercício 2 — Produto × Processo"
    Liste duas características de qualidade de **produto** e duas de **processo**.
    Explique, em uma frase cada, por que melhorar o processo tende a melhorar o
    produto. Entregue em `respostas/ex02.md`.

??? abstract "Exercício 3 — Shift-left (com código)"
    Escreva uma classe `ClassificadorTermos` em Java com um método
    `classificar(String situacao)` que devolva `"defeito"`, `"erro"` ou `"falha"`
    para pelo menos três frases de exemplo. Explique no `README` por que achar
    defeitos cedo é mais barato.

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** e nomeado `una-gqs-lista01`.
    - [ ] `README.md` com seu **nome completo** e índice das respostas.
    - [ ] Pelo menos **2 commits** com mensagens claras.
    - [ ] Código Java **compila** sem erros.
    - [ ] Link entregue no **Google Classroom** antes do prazo.
