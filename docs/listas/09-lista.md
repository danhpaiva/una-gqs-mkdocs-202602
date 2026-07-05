# Lista 09 — Plano e Roteiro de Testes

!!! abstract "🎯 Missão"
    Produzir um **plano de testes** enxuto e uma **matriz de rastreabilidade** para
    uma funcionalidade, transformando casos de teste em testes automatizados.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** chamado **`una-gqs-lista09`**.
2. **Clone**:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista09.git
    cd una-gqs-lista09
    ```
3. Escreva o plano em `plano/` e o código/testes em `src/`.
4. **Suba**:
    ```bash
    git add .
    git commit -m "docs: adiciona plano e roteiro de testes da lista 09"
    git push origin main
    ```
5. **Entregue o link** no **Google Classroom**.

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista09/
├── README.md
├── plano/
│   ├── plano-de-testes.md
│   ├── casos-de-teste.md
│   └── rastreabilidade.md
└── src/
    ├── main/java/AuthService.java
    └── test/java/AuthServiceTest.java
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Plano de testes"
    Escreva um plano enxuto para uma funcionalidade de **login**, contendo: objetivo,
    escopo, itens a testar, **critérios de entrada e saída**, ambiente e riscos.

??? abstract "Exercício 2 — Casos de teste completos"
    Escreva **três** casos de teste para o login (sucesso, senha incorreta, usuário
    inexistente) com todos os campos: ID, pré-condição, passos, dados, resultado
    esperado.

??? abstract "Exercício 3 — Rastreabilidade + automação"
    Monte uma **matriz de rastreabilidade** ligando os requisitos aos casos de teste
    e automatize **pelo menos um** dos casos em JUnit (`AuthServiceTest`).

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** `una-gqs-lista09`.
    - [ ] Plano de testes com critérios de **entrada e saída** objetivos.
    - [ ] Casos de teste com resultado esperado **específico e verificável**.
    - [ ] Matriz de rastreabilidade e ao menos 1 teste automatizado.
    - [ ] Link entregue no **Google Classroom** antes do prazo.
