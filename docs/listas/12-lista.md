# Lista 12 — Configuração, Manutenção e Reengenharia

!!! abstract "🎯 Missão"
    Praticar **gestão de configuração** com Git (branches, tags, SemVer),
    classificar **tipos de manutenção** e diferenciar reengenharia, engenharia
    reversa e refatoração.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** chamado **`una-gqs-lista12`**.
2. **Clone**:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista12.git
    cd una-gqs-lista12
    ```
3. Faça o fluxo com **branch + tag** e documente em `respostas/`.
4. **Suba** (incluindo uma tag de versão):
    ```bash
    git add .
    git commit -m "chore: prepara entrega da lista 12"
    git tag v1.0.0
    git push origin main --tags
    ```
5. **Entregue o link** no **Google Classroom**.

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista12/
├── README.md
├── src/
│   └── CalculadoraImposto.java   # antes e depois da refatoração
└── respostas/
    ├── tipos-de-manutencao.md
    ├── semver.md
    └── reengenharia.md
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Fluxo de configuração com Git"
    Crie uma branch `feature/melhoria`, faça um commit, abra o **merge** na `main` e
    marque uma **tag** `v1.0.0`. Documente os comandos usados e explique o que é uma
    **baseline**.

??? abstract "Exercício 2 — Tipos de manutenção e SemVer"
    Classifique como corretiva, adaptativa, perfectiva ou preventiva:

    1. O cliente pediu um novo relatório.
    2. Uma nova lei obriga a mudar o cálculo do imposto.
    3. Corrigir uma divisão por zero relatada por um usuário.
    4. Reescrever um módulo confuso antes que dê problema.

    Depois, dada a versão `1.4.2`, diga a próxima versão para (a) correção de bug,
    (b) nova funcionalidade compatível, (c) mudança que quebra a API.

??? abstract "Exercício 3 — Refatoração protegida por testes"
    Pegue um método confuso (`CalculadoraImposto`), escreva um teste que fixe seu
    comportamento e **refatore** melhorando nomes e estrutura sem quebrar o teste.
    Explique a diferença entre **reengenharia**, **engenharia reversa** e
    **refatoração**.

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** `una-gqs-lista12`.
    - [ ] Uso de **branch** e **tag** (`v1.0.0`) evidenciado.
    - [ ] Tipos de manutenção classificados corretamente.
    - [ ] Refatoração com teste que garante o comportamento.
    - [ ] Link entregue no **Google Classroom** antes do prazo.
