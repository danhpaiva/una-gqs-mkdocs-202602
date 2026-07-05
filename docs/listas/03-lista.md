# Lista 03 — Revisão e Inspeção

!!! abstract "🎯 Missão"
    Aplicar **técnicas de revisão** na prática: revisar um código com defeitos
    usando um checklist e simular uma inspeção formal com papéis definidos.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** chamado **`una-gqs-lista03`**.
2. **Clone**:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista03.git
    cd una-gqs-lista03
    ```
3. Coloque o código a revisar em `src/` e os relatórios em `revisao/`.
4. **Suba**:
    ```bash
    git add .
    git commit -m "docs: adiciona relatorio de revisao da lista 03"
    git push origin main
    ```
5. **Entregue o link** no **Google Classroom**.

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista03/
├── README.md
├── src/
│   └── CalculadoraFolha.java   # código com defeitos a revisar
└── revisao/
    ├── checklist.md
    ├── defeitos-encontrados.md
    └── inspecao-papeis.md
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Revisão com checklist"
    Coloque em `src/` um código Java (pode ser o fornecido pelo professor ou um seu
    com defeitos propositais). Aplique um **checklist** de revisão e registre em
    `revisao/defeitos-encontrados.md` **pelo menos 5 problemas** (nomes, tratamento
    de erro, números mágicos, código morto, etc.).

??? abstract "Exercício 2 — Escolha a técnica"
    Para cada cenário, escolha entre **informal**, **walkthrough** e **inspeção
    formal** e justifique:

    1. Ajuste rápido de uma mensagem de erro.
    2. Módulo de cálculo de juros de um banco.
    3. Apresentar a arquitetura de um serviço novo ao time.

??? abstract "Exercício 3 — Simulação de inspeção"
    Em `revisao/inspecao-papeis.md`, descreva como seria uma inspeção de Fagan do
    seu código: quem seria **moderador, autor, leitor, inspetores e escriba**, e
    por que o autor **não** conserta os defeitos durante a reunião.

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** `una-gqs-lista03`.
    - [ ] Checklist de revisão documentado.
    - [ ] Pelo menos **5 defeitos** registrados com localização e sugestão.
    - [ ] Papéis da inspeção descritos.
    - [ ] Link entregue no **Google Classroom** antes do prazo.
