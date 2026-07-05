# Lista 08 — Níveis de Teste

!!! abstract "🎯 Missão"
    Distinguir na prática os **níveis de teste** (unitário, integração, sistema,
    validação) e as estratégias de integração, escrevendo testes de mais de um
    nível.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** chamado **`una-gqs-lista08`**.
2. **Clone**:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista08.git
    cd una-gqs-lista08
    ```
3. Escreva testes unitários e de integração em `src/test`.
4. **Suba**:
    ```bash
    git add .
    git commit -m "test: adiciona testes unitario e de integracao da lista 08"
    git push origin main
    ```
5. **Entregue o link** no **Google Classroom**.

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista08/
├── README.md
├── pom.xml
└── src/
    ├── main/java/
    │   ├── CarrinhoService.java
    │   └── RepositorioProdutos.java
    └── test/java/
        ├── CarrinhoServiceTest.java     # unitário
        └── CarrinhoIntegracaoTest.java  # integração
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Classifique o nível"
    Diga o nível de teste de cada caso e justifique:

    1. Verificar se `formatarCpf` devolve `123.456.789-00`.
    2. Conferir se o cadastro **salva de fato** no repositório.
    3. Cliente navegar no sistema inteiro e aprovar antes do lançamento.

??? abstract "Exercício 2 — Unitário + integração (código)"
    Implemente um `CarrinhoService` que usa um `RepositorioProdutos`. Escreva:

    - um **teste unitário** isolando o serviço (com mock do repositório);
    - um **teste de integração** usando o repositório real (em memória).

    Explique no `README` a diferença entre os dois.

??? abstract "Exercício 3 — Estratégias de integração"
    Explique **top-down** e **bottom-up**. Diga o que são **stub** e **driver** e
    em qual estratégia cada um é usado. Dê um exemplo de quando escolheria cada
    abordagem.

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** `una-gqs-lista08`.
    - [ ] Um teste **unitário** e um de **integração** rodando.
    - [ ] Classificação de níveis correta e justificada.
    - [ ] Explicação de stub × driver.
    - [ ] Link entregue no **Google Classroom** antes do prazo.
