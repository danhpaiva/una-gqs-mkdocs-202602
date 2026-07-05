# Lista 07 — TDD e Testes Automatizados

!!! abstract "🎯 Missão"
    Escrever seus primeiros **testes automatizados com JUnit 5**, praticando o
    ciclo **Red-Green-Refactor** e o padrão **AAA**.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** chamado **`una-gqs-lista07`**.
2. **Clone**:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista07.git
    cd una-gqs-lista07
    ```
3. Crie um projeto Maven/Gradle com JUnit 5. Escreva **o teste antes** do código.
4. **Suba** mostrando o histórico do ciclo TDD nos commits:
    ```bash
    git add .
    git commit -m "test: adiciona teste que falha (red) para ehPar"
    git commit -m "feat: implementa ehPar ate o teste passar (green)"
    git push origin main
    ```
5. **Entregue o link** no **Google Classroom**.

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista07/
├── README.md
├── pom.xml                       # ou build.gradle
└── src/
    ├── main/java/
    │   └── Calculadora.java
    └── test/java/
        └── CalculadoraTest.java
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Ciclo TDD"
    Implemente `ehPar(int)` usando **Red-Green-Refactor**. Faça commits separados
    para o teste que falha (red) e o código que faz passar (green). Descreva o
    ciclo no `README`.

??? abstract "Exercício 2 — Testes no padrão AAA"
    Crie uma classe `Conta` que não permite saque maior que o saldo (lança
    `SaldoInsuficienteException`). Escreva **pelo menos 3 testes** JUnit no padrão
    **Arrange-Act-Assert**, incluindo o caso de erro com `assertThrows`.

??? abstract "Exercício 3 — Dublê de teste (mock)"
    Crie um `PedidoService` que depende de uma interface `Estoque`. Use **Mockito**
    para simular estoque indisponível e verifique que o serviço rejeita o pedido.
    Explique no `README` por que mockar `Estoque` faz sentido aqui.

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** `una-gqs-lista07`.
    - [ ] Testes JUnit **rodando e passando** (`mvn test` verde).
    - [ ] Commits evidenciando o ciclo **red → green**.
    - [ ] Pelo menos um teste com `assertThrows` e um com **mock**.
    - [ ] Link entregue no **Google Classroom** antes do prazo.
