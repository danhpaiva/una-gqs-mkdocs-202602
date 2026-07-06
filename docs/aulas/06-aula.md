# Aula 06 — Teste de Caixa Preta (Funcional)

!!! info "Objetivos da aula"
    - Entender o **teste de caixa preta** (funcional) e quando usá-lo.
    - Aplicar **particionamento de equivalência**.
    - Aplicar **análise de valor-limite**.
    - Conhecer **tabela de decisão** e **transição de estados**.

## Fechando a caixa

No teste de **caixa preta**, ignoramos o código. Olhamos apenas o que **entra** e
o que **deve sair**, segundo a **especificação**. É como testar um forno: você não
abre para ver a resistência, você põe o bolo e vê se assa.

!!! success "Vantagem"
    Independe da implementação. Os testes continuam válidos mesmo que o código
    seja reescrito por dentro — desde que o comportamento externo seja o mesmo.

## Particionamento de equivalência

A ideia: dividir as entradas em **classes** que o software deve tratar do mesmo
jeito. Se um valor da classe funciona, presumimos que todos funcionam — então
basta **um representante** por classe.

!!! example "Idade para uma bolsa (18 a 25 anos)"
    | Classe | Faixa | Válida? | Representante |
    | :--- | :--- | :--- | :--- |
    | Abaixo | idade < 18 | ❌ inválida | 15 |
    | Dentro | 18 ≤ idade ≤ 25 | ✅ válida | 21 |
    | Acima | idade > 25 | ❌ inválida | 30 |

    Em vez de testar 15, 16, 17, 18, 19... testamos **um** de cada classe.

!!! tip "Não esqueça as classes inválidas"
    O erro mais comum é testar só o que **deveria funcionar**. Para cada entrada,
    pense em partições válidas **e** inválidas de vários tipos:

    - **Fora da faixa** (menor/maior que o permitido).
    - **Formato errado** (letra onde se espera número, tamanho errado).
    - **Ausência** (campo vazio, `null`).
    - **Tipo/valor especial** (zero, negativo, caractere especial).

    Cada partição inválida costuma ter um **tratamento** diferente — por isso conta
    como uma classe separada.

## Análise de valor-limite

Defeitos adoram **fronteiras** (`>` vs `>=`). Por isso testamos os **limites** de
cada partição válida — e seus vizinhos imediatos.

```mermaid
flowchart LR
    A[17: inválido] --- B[18: limite ✅]
    B --- C[25: limite ✅]
    C --- D[26: inválido]
```

!!! example "Limites para a faixa 18–25"
    Casos essenciais: **17, 18, 25, 26** (as bordas e seus vizinhos).

    ```java
    @Test void limiteInferiorValido()   { assertTrue(elegivel(18)); }
    @Test void abaixoDoLimite()          { assertFalse(elegivel(17)); }
    @Test void limiteSuperiorValido()    { assertTrue(elegivel(25)); }
    @Test void acimaDoLimite()           { assertFalse(elegivel(26)); }
    ```

!!! note "Duas escolas: 2 valores × 3 valores"
    - **Análise de 2 valores:** testa o **limite** e seu **vizinho imediato** (para
      18: os valores 17 e 18). Mais enxuta.
    - **Análise de 3 valores:** testa o valor **antes**, o **limite** e o **depois**
      (17, 18, 19). Mais rigorosa, pega defeitos de `>` vs `>=` vs `==`.

    Combine equivalência **e** limite: a equivalência garante que cada classe é
    coberta; o limite reforça as **fronteiras**, onde os defeitos se concentram.

!!! example "Aplicando a um campo de tamanho fixo (ex.: 8 dígitos)"
    Quando a regra é sobre **tamanho** (um CEP de 8 dígitos, por exemplo), as
    partições e limites são sobre a **quantidade de caracteres**:

    | Classe | Exemplo | Válida? |
    | :--- | :--- | :--- |
    | 7 dígitos (curto) | `"1234567"` | ❌ |
    | **8 dígitos** (limite) | `"12345678"` | ✅ |
    | 9 dígitos (longo) | `"123456789"` | ❌ |
    | 8 caracteres com letra (formato) | `"1234abcd"` | ❌ |
    | vazio / `null` | `""` | ❌ |

    Os limites de tamanho a testar são **7, 8 e 9**.

## Tabela de decisão

Útil quando a saída depende de **combinações** de condições.

!!! example "Desconto: cliente VIP e compra acima de R$ 100"
    | Regra | VIP? | Compra > 100? | Desconto |
    | :--- | :--- | :--- | :--- |
    | R1 | Não | Não | 0% |
    | R2 | Não | Sim | 5% |
    | R3 | Sim | Não | 10% |
    | R4 | Sim | Sim | 15% |

    Cada **regra** vira (ao menos) um caso de teste.

!!! tip "Montando uma tabela de decisão"
    1. Liste as **condições** (entradas booleanas). Com $n$ condições há $2^n$
       combinações.
    2. Liste as **ações** (saídas).
    3. Preencha uma coluna (regra) por combinação.
    4. **Simplifique**: se uma ação não depende de uma condição, marque-a como
       "indiferente" (—) e junte regras redundantes.

    Para "empréstimo aprovado se renda > R\$ 3.000 **E** score > 700", há 2
    condições → 4 regras. Só a combinação **V + V** aprova; as outras três negam.

## Transição de estados

Quando o sistema tem **estados** e o comportamento depende da história (não só da
entrada atual), modelamos as transições.

```mermaid
stateDiagram-v2
    [*] --> Rascunho
    Rascunho --> Publicado: publicar()
    Publicado --> Arquivado: arquivar()
    Arquivado --> Publicado: republicar()
```

Testamos **transições válidas** (Rascunho → Publicado) e também **inválidas**
(tentar arquivar um rascunho deve ser rejeitado).

!!! note "O que cobrir em uma máquina de estados"
    - **Cada estado** é alcançado ao menos uma vez.
    - **Cada transição válida** é exercitada (cobertura conhecida como *0-switch*).
    - **Transições inválidas** são **rejeitadas** — o sistema deve permanecer no
      estado atual (ou dar erro), nunca "pular" para um estado indevido.

    Exemplo de e-commerce: `Novo → Pago → Enviado → Entregue` são válidas; tentar
    `Novo → Entregue` (entregar sem pagar) é uma transição **inválida** que deve ser
    bloqueada.

## Caixa branca × caixa preta: complementares

=== "Use caixa branca quando..."
    Quer garantir que os **caminhos internos** e casos raros do código foram
    exercitados (Aula 05).

=== "Use caixa preta quando..."
    Quer validar **requisitos** e comportamento visível, sem depender da
    implementação.

!!! tip "Na prática, use as duas"
    Times maduros combinam: caixa preta guiada pela especificação **e** medição de
    cobertura (caixa branca) para achar buracos.

## Exercícios

??? abstract "Exercício 1 — Partições e limites"
    Um campo aceita **CEP com 8 dígitos**. Defina as classes de equivalência
    (válidas e inválidas) e os valores-limite que você testaria.

??? abstract "Exercício 2 — Tabela de decisão"
    Monte a tabela de decisão para: *um empréstimo é aprovado se o cliente tem
    renda acima de R$ 3.000 **e** score acima de 700*. Liste os casos de teste.

??? abstract "Exercício 3 — Transição de estados"
    Modele os estados de um pedido de e-commerce (ex.: Novo → Pago → Enviado →
    Entregue) e aponte **uma** transição inválida que deveria ser bloqueada.

## Referências

**Leitura base**

- MYERS, G. J.; SANDLER, C.; BADGETT, T. *The Art of Software Testing*. 3. ed.
  Wiley, 2011 — particionamento de equivalência e valor-limite.
- PRESSMAN, R. S.; MAXIM, B. R. *Engenharia de Software*. 8. ed. AMGH, 2016 —
  cap. sobre teste de caixa preta.

**Normas e definições**

- ISTQB — *Foundation Level Syllabus* (técnicas baseadas em especificação):
  <https://www.istqb.org/>.
- BS 7925-2 / ISO/IEC/IEEE 29119 — técnicas de projeto de casos de teste.

!!! tip "Próxima Parada 🚀"
    Pratique na [**Lista 06 — Caixa Preta**](../listas/06-lista.md).
    Na próxima aula automatizamos tudo isso com **TDD e testes automatizados**.
