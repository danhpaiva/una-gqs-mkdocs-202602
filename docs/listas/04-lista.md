# Lista 04 — Fundamentos e Estratégias de Teste

!!! abstract "🎯 Missão"
    Fixar os fundamentos do teste: princípios, **verificação × validação**, teste ×
    depuração e a escrita de **casos de teste** claros.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** chamado **`una-gqs-lista04`**.
2. **Clone**:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista04.git
    cd una-gqs-lista04
    ```
3. Escreva as respostas em Markdown e o código em `src/`.
4. **Suba**:
    ```bash
    git add .
    git commit -m "docs: resolve fundamentos de teste da lista 04"
    git push origin main
    ```
5. **Entregue o link** no **Google Classroom**.

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista04/
├── README.md
├── respostas/
│   ├── verificacao-validacao.md
│   ├── principios.md
│   └── casos-de-teste.md
└── src/
    └── ValidadorIdade.java
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Verificação ou validação"
    Classifique e justifique:

    1. Rodar os testes unitários no CI.
    2. Cliente usar o sistema por uma semana e dar feedback.
    3. Conferir se o código segue a especificação de requisitos.

??? abstract "Exercício 2 — Princípios do teste"
    Explique o **paradoxo do pesticida** e o princípio de que **teste exaustivo é
    impossível**. Dê um exemplo numérico do porquê testar todas as entradas de uma
    soma de dois inteiros é inviável.

??? abstract "Exercício 3 — Casos de teste (com código)"
    Escreva a classe `ValidadorIdade` (regra: elegível se `18 ≤ idade ≤ 65`) e
    documente **em tabela** pelo menos 4 casos de teste (entrada, ação, resultado
    esperado), incluindo valores válidos e inválidos.

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** `una-gqs-lista04`.
    - [ ] Respostas de verificação × validação corretas e justificadas.
    - [ ] Tabela de casos de teste com entrada, ação e resultado esperado.
    - [ ] Código Java compilando.
    - [ ] Link entregue no **Google Classroom** antes do prazo.
