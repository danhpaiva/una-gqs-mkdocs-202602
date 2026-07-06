# Aula 05 — Teste de Caixa Branca (Estrutural)

!!! info "Objetivos da aula"
    - Entender o que é **teste de caixa branca** (estrutural).
    - Conhecer os **critérios de cobertura**: comando, decisão, condição, caminho.
    - Calcular a **complexidade ciclomática** de McCabe.
    - Derivar casos de teste a partir do **grafo de fluxo de controle**.

## Olhando dentro da caixa

No teste de **caixa branca** (também dito *estrutural*, *caixa de vidro* ou
*caixa transparente*), conhecemos e usamos a **estrutura interna** do código para
projetar os testes. A pergunta é: *"todos os caminhos importantes do código foram
exercitados?"*

=== "Caixa Branca (esta aula)"
    Baseia-se no **código**. Objetivo: **cobrir** comandos, decisões e caminhos.
    Quem faz costuma ser quem programa.

=== "Caixa Preta (próxima aula)"
    Baseia-se na **especificação**, ignorando o código. Objetivo: cobrir
    **entradas e saídas** esperadas.

## Critérios de cobertura

Do mais fraco ao mais forte:

| Critério | Exige que... | Força |
| :--- | :--- | :--- |
| **Comando** *(statement)* | toda linha execute ao menos 1 vez | fraca |
| **Decisão** *(branch)* | todo `if/while` seja testado **verdadeiro e falso** | média |
| **Condição** | cada subcondição booleana assuma V e F | forte |
| **Caminho** *(path)* | todo caminho independente seja percorrido | mais forte |

!!! warning "100% de comando não basta"
    Cobrir todas as **linhas** não garante cobrir todas as **decisões**. Um `if`
    sem `else` pode ter a linha de dentro executada e, ainda assim, o ramo "falso"
    nunca ser testado.

!!! example "100% de comando, só 50% de decisão"
    ```java
    int abs(int x) {
        int r = x;          // executa sempre
        if (x < 0) {        // decisão
            r = -x;         // executa só quando x < 0
        }
        return r;           // executa sempre
    }
    ```
    Um único teste com `x = -5` executa **todas as linhas** (100% de comando). Mas
    a decisão `x < 0` só foi testada no ramo **verdadeiro** — o ramo **falso**
    (`x >= 0`) nunca rodou. Cobertura de decisão = 50%. Para chegar a 100% de
    decisão preciso de **dois** casos: um com `x < 0` e outro com `x >= 0`.

### Cobertura de decisão × condição em expressões compostas

Quando a decisão tem **operadores lógicos** (`&&`, `||`), decisão e condição
divergem. Considere `if (a && b)`:

- **Cobertura de decisão** só exige que o `if` inteiro dê **verdadeiro** e **falso**
  (2 casos).
- **Cobertura de condição** exige que **cada** subcondição (`a` e `b`) assuma
  verdadeiro e falso individualmente.

!!! note "Curto-circuito importa"
    Em Java, `&&` e `||` fazem **curto-circuito**: em `a && b`, se `a` for falso,
    `b` **nem é avaliado**. Isso afeta quais combinações são alcançáveis e é a razão
    de cada operador lógico contar como um **ponto de decisão** extra no cálculo da
    complexidade (a seguir).

## Grafo de fluxo de controle

Transformamos o código em um grafo: **nós** são comandos e **arestas** são
desvios de fluxo.

```java
public String classificar(int n) {          // 1
    if (n > 0) {                             // 2
        return "positivo";                   // 3
    } else if (n < 0) {                      // 4
        return "negativo";                   // 5
    }
    return "zero";                           // 6
}
```

```mermaid
flowchart TD
    N2{n > 0?} -->|V| N3[positivo]
    N2 -->|F| N4{n < 0?}
    N4 -->|V| N5[negativo]
    N4 -->|F| N6[zero]
```

## Complexidade ciclomática (McCabe)

Mede o número de **caminhos independentes** — e, na prática, um bom **número
mínimo de casos de teste** para cobrir as decisões. Três formas de calcular:

$$
V(G) = E - N + 2 \qquad\text{ou}\qquad V(G) = P + 1
$$

Onde $E$ = arestas, $N$ = nós e $P$ = número de **pontos de decisão** (predicados).

!!! example "Calculando para o exemplo"
    O método `classificar` tem **2 decisões** (`n > 0` e `n < 0`), logo:

    $$V(G) = P + 1 = 2 + 1 = 3$$

    Precisamos de **3 casos** para cobrir as decisões: um positivo, um negativo e
    o zero.

!!! tip "Como contar P (pontos de decisão)"
    Uma forma prática: conte **cada condição atômica** (cada comparação booleana
    simples). Isso equivale a somar `if`/`while`/`for`/`case` **mais** cada operador
    lógico `&&`/`||`. Exemplos:

    - `if (x > 0)` → 1 condição → $V(G) = 1 + 1 = 2$.
    - `if (idade >= 18 && temHabilitacao)` → 2 condições (`idade >= 18` e
      `temHabilitacao`) → $V(G) = 2 + 1 = 3$.
    - `while (a) { if (b || c) {...} }` → 3 condições (`a`, `b`, `c`) →
      $V(G) = 3 + 1 = 4$.

    Contar as condições atômicas alinha $V(G)$ ao esforço real de cobrir as
    **decisões compostas**, não só os ramos externos.

## Derivando os casos de teste

```java
@Test void positivo() { assertEquals("positivo", classificar(7)); }
@Test void negativo() { assertEquals("negativo", classificar(-3)); }
@Test void zero()     { assertEquals("zero", classificar(0)); }
```

!!! tip "Cobertura como métrica, não como meta"
    Ferramentas como **JaCoCo** medem cobertura no Java. Alta cobertura é bom
    sinal, mas 100% de cobertura com asserts fracos ainda deixa passar defeitos.
    Cobertura mostra o que **não** foi testado, não que o teste é **bom**.

## Um roteiro para derivar casos pela estrutura

Diante de um método, siga sempre os mesmos passos:

1. **Numere** os comandos e desenhe o **grafo de fluxo** (nós = comandos, arestas =
   desvios).
2. **Conte** os pontos de decisão e calcule $V(G)$ — ele dá o número **mínimo** de
   casos para cobrir as decisões.
3. **Liste os caminhos** que cobrem cada ramo verdadeiro e falso.
4. **Escolha entradas** que forcem cada caminho.
5. **Escreva o resultado esperado** de cada caso e transforme em teste JUnit.

!!! example "Aplicando a uma validação de senha (≥ 8 caracteres **E** ≥ 1 número)"
    A condição `senha.length() >= 8 && temNumero(senha)` tem **2 condições** →
    $V(G) = 3$. Para cobrir as decisões precisamos exercitar cada subcondição em
    verdadeiro e falso:

    | Caso | Entrada | `≥ 8`? | tem número? | Esperado |
    | :--- | :--- | :--- | :--- | :--- |
    | 1 | `"abc123xy"` | ✅ | ✅ | válida |
    | 2 | `"abc1"` | ❌ | ✅ | inválida (curta) |
    | 3 | `"abcdefgh"` | ✅ | ❌ | inválida (sem número) |

    Três casos cobrem todos os ramos — exatamente o $V(G)$ calculado.

## Exercícios

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

??? abstract "Exercício 2 — Comando x decisão"
    Escreva um trecho de código com um `if` sem `else` em que **100% de cobertura
    de comando** seja atingida, mas a cobertura de **decisão** seja apenas 50%.

??? abstract "Exercício 3 — Do grafo aos testes"
    Desenhe o grafo de fluxo e liste os casos de teste necessários para cobrir
    **todas as decisões** de uma função que valida uma senha (mínimo 8 caracteres
    **e** ao menos um número).

## Referências

**Leitura base**

- PRESSMAN, R. S.; MAXIM, B. R. *Engenharia de Software*. 8. ed. AMGH, 2016 —
  cap. sobre teste de caixa branca e teste de caminho básico.
- SOMMERVILLE, Ian. *Engenharia de Software*. 10. ed. Pearson, 2019 — cap. 8.

**Artigo clássico**

- McCABE, T. J. *A Complexity Measure*. IEEE Transactions on Software Engineering,
  1976 — origem da complexidade ciclomática.

**Ferramenta**

- JaCoCo — cobertura de código para Java: <https://www.jacoco.org/jacoco/>.

!!! tip "Próxima Parada 🚀"
    Exercite a estrutura na [**Lista 05 — Caixa Branca**](../listas/05-lista.md).
    Na próxima aula fechamos a caixa e olhamos só entradas e saídas: **caixa preta**.
