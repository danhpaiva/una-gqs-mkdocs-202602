# Aula 04 — Fundamentos e Estratégias de Teste

!!! info "Objetivos da aula"
    - Entender **o que é** e **para que serve** o teste de software.
    - Conhecer os **princípios** do teste (por que testar tudo é impossível).
    - Diferenciar **verificação** de **validação**.
    - Ter a visão geral das **estratégias** e da relação teste × depuração.

## O que é testar (e o que não é)

Testar é **executar** o software com a intenção de **encontrar defeitos**. Um bom
teste é aquele que tem **alta chance de revelar um defeito ainda desconhecido**.

!!! quote "Dijkstra"
    "O teste pode mostrar a **presença** de defeitos, mas nunca a sua **ausência**."

Ou seja: passar em todos os testes não prova que o software é perfeito — prova que
os defeitos que **procuramos** não estão lá.

## Sete princípios do teste

??? note "Clique para ver os 7 princípios (ISTQB)"
    1. Teste mostra presença de defeitos, não ausência.
    2. **Teste exaustivo é impossível** — foque no que importa.
    3. **Teste cedo** economiza (shift-left).
    4. Defeitos se **agrupam** (poucos módulos concentram a maioria).
    5. **Paradoxo do pesticida:** repetir os mesmos testes para de achar defeitos novos.
    6. Teste **depende do contexto** (um jogo ≠ um sistema hospitalar).
    7. A ausência de erros é uma **ilusão** se o software não atende à necessidade.

!!! warning "Teste exaustivo é impossível"
    Uma função que soma dois `int` de 32 bits tem $2^{32} \times 2^{32} \approx
    1{,}8 \times 10^{19}$ combinações de entrada. Testar todas levaria séculos.
    Por isso precisamos de **técnicas** para escolher poucos casos que valem por
    muitos (Aulas 05 e 06).

## Verificação × Validação

Dois conceitos que caem em prova e vivem confundidos:

=== "Verificação"
    *"Estamos construindo o produto **corretamente**?"*
    Conferimos se o software está de acordo com a **especificação**. Ex.: revisões,
    testes de unidade.

=== "Validação"
    *"Estamos construindo o produto **certo**?"*
    Conferimos se o software atende à **necessidade real** do usuário. Ex.: teste
    de aceitação com o cliente.

| | Verificação | Validação |
| :--- | :--- | :--- |
| Pergunta | Certo do jeito certo? | Certo o produto certo? |
| Referência | Especificação | Necessidade do usuário |
| Quando | Ao longo do desenvolvimento | Perto/depois da entrega |

## Teste × Depuração (debugging)

Não são a mesma atividade:

```mermaid
flowchart LR
    A[Teste] -->|encontra uma falha| B[Depuração]
    B -->|localiza o defeito| C[Correção]
    C -->|reteste| A
```

- **Teste**: revela que **existe** um problema (uma falha).
- **Depuração**: descobre **onde** está o defeito e o corrige.

## Estratégia geral: do menor ao maior

A estratégia clássica organiza o teste em níveis, começando pequeno e crescendo
(veremos em detalhe na Aula 08):

```mermaid
flowchart TB
    U[Unitário] --> I[Integração]
    I --> S[Sistema]
    S --> A[Aceitação/Validação]
```

!!! example "Meu primeiro caso de teste"
    Um **caso de teste** define entrada, ação e resultado esperado:

    ```java
    @Test
    void deveRejeitarIdadeNegativa() {
        var cadastro = new Cadastro();
        assertThrows(IllegalArgumentException.class,
            () -> cadastro.definirIdade(-1));
    }
    ```

## Exercícios

??? abstract "Exercício 1 — Verificação ou validação?"
    Classifique:

    1. Rodar os testes unitários no CI.
    2. Cliente usar o sistema por uma semana e dar feedback.
    3. Conferir se o código segue a especificação de requisitos.

??? abstract "Exercício 2 — Paradoxo do pesticida"
    Explique o que é o paradoxo do pesticida e cite **uma** forma de combatê-lo na
    prática.

??? abstract "Exercício 3 — Teste x depuração"
    Descreva um cenário curto (3–4 passos) que comece com um teste falhando e
    termine com um reteste passando. Diga onde acaba o teste e começa a depuração.

!!! tip "Próxima Parada 🚀"
    Consolide os fundamentos na [**Lista 04 — Estratégias de Teste**](../listas/04-lista.md).
    Na próxima aula abrimos a "caixa": o **teste de caixa branca**.
