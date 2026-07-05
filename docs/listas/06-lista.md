# Lista 06 — Teste de Caixa Preta

!!! abstract "🎯 Missão"
    Aplicar técnicas **funcionais**: particionamento de equivalência, análise de
    valor-limite e tabela de decisão — projetando testes a partir da especificação.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** chamado **`una-gqs-lista06`**.
2. **Clone**:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista06.git
    cd una-gqs-lista06
    ```
3. Documente as técnicas em `respostas/` e coloque o código em `src/`.
4. **Suba**:
    ```bash
    git add .
    git commit -m "test: adiciona analise de caixa preta da lista 06"
    git push origin main
    ```
5. **Entregue o link** no **Google Classroom**.

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista06/
├── README.md
├── src/
│   └── ElegibilidadeBolsa.java
└── respostas/
    ├── particoes-e-limites.md
    └── tabela-decisao.md
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Partições e valor-limite"
    Uma bolsa exige idade entre **18 e 25 anos**. Defina as **classes de
    equivalência** (válidas e inválidas) e os **valores-limite** que você testaria.
    Implemente `ElegibilidadeBolsa.elegivel(int idade)` em Java.

??? abstract "Exercício 2 — Tabela de decisão"
    Monte a tabela de decisão para: *um empréstimo é aprovado se a renda for maior
    que R$ 3.000 **e** o score for maior que 700*. Liste todas as regras e o caso
    de teste correspondente a cada uma.

??? abstract "Exercício 3 — Transição de estados"
    Modele os estados de um pedido de e-commerce (Novo → Pago → Enviado → Entregue)
    com um diagrama e aponte **uma** transição inválida que deveria ser bloqueada.

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** `una-gqs-lista06`.
    - [ ] Classes de equivalência e valores-limite claramente identificados.
    - [ ] Tabela de decisão completa com casos de teste.
    - [ ] Diagrama de estados incluído.
    - [ ] Link entregue no **Google Classroom** antes do prazo.
