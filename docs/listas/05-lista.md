# Lista 05 — Teste de Caixa Branca

!!! abstract "🎯 Missão"
    Aplicar teste **estrutural**: desenhar o grafo de fluxo, calcular a
    **complexidade ciclomática** e derivar casos de teste que cubram as decisões.

## 🚀 Passo a passo da entrega

1. **Crie um repositório público** chamado **`una-gqs-lista05`**.
2. **Clone**:
    ```bash
    git clone https://github.com/SEU_USUARIO/una-gqs-lista05.git
    cd una-gqs-lista05
    ```
3. Coloque o código em `src/`, os grafos em `grafos/` e a análise em `respostas/`.
4. **Suba**:
    ```bash
    git add .
    git commit -m "test: adiciona analise de caixa branca da lista 05"
    git push origin main
    ```
5. **Entregue o link** no **Google Classroom**.

## 📁 Estrutura de pastas sugerida

```text
una-gqs-lista05/
├── README.md
├── src/
│   └── Classificador.java
├── grafos/
│   └── fluxo-classificar.md   # diagrama (Mermaid ou imagem)
└── respostas/
    └── complexidade.md
```

## 🧩 Exercícios

??? abstract "Exercício 1 — Complexidade ciclomática"
    Calcule $V(G)$ para o método abaixo e diga o número mínimo de casos de teste:

    ```java
    boolean podeDirigir(int idade, boolean temHabilitacao) {
        if (idade >= 18 && temHabilitacao) {
            return true;
        }
        return false;
    }
    ```

??? abstract "Exercício 2 — Grafo e cobertura de decisão"
    Escreva em `src/` um método `classificar(int n)` (positivo/negativo/zero),
    desenhe seu **grafo de fluxo de controle** e liste os casos de teste que cobrem
    **todas as decisões**.

??? abstract "Exercício 3 — Comando × decisão"
    Escreva um trecho com um `if` **sem** `else` em que a cobertura de **comando**
    seja 100% mas a de **decisão** seja apenas 50%. Explique por que isso acontece.

## ✅ Checklist de qualidade

!!! check "Antes de entregar, confirme"
    - [ ] Repositório **público** `una-gqs-lista05`.
    - [ ] Cálculo de $V(G)$ mostrado passo a passo.
    - [ ] Grafo de fluxo incluído (diagrama ou imagem).
    - [ ] Casos de teste cobrindo todas as decisões.
    - [ ] Link entregue no **Google Classroom** antes do prazo.
