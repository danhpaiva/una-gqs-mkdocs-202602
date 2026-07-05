# Aula 07 — TDD e Testes Automatizados

!!! info "Objetivos da aula"
    - Entender o ciclo **Red-Green-Refactor** do TDD.
    - Escrever testes automatizados com **JUnit 5**.
    - Conhecer **asserts**, dublês de teste (**mocks**) e boas práticas (AAA).
    - Ligar os testes ao **pipeline de CI** (Aula 02).

## Por que automatizar?

Teste manual não escala: repetir 200 verificações a cada mudança é inviável.
Testes **automatizados** rodam em segundos, sempre do mesmo jeito, e podem ser
disparados pelo CI a cada `push`.

```mermaid
flowchart LR
    A[Mudança no código] --> B[Testes automatizados rodam]
    B --> C{Tudo verde?}
    C -->|Sim| D[Segue o fluxo]
    C -->|Não| E[Corrige antes de avançar]
```

## TDD: teste primeiro

**Test-Driven Development** inverte a ordem: você escreve o **teste antes** do
código de produção. O ciclo é curto e repetido:

```mermaid
flowchart LR
    R[🔴 Red: escreve teste que falha] --> G[🟢 Green: faz passar do jeito mais simples]
    G --> Rf[🔵 Refactor: melhora sem quebrar]
    Rf --> R
```

=== "🔴 Red"
    Escreva um teste para um comportamento que **ainda não existe**. Ele **deve
    falhar** — se passar, o teste está errado.

=== "🟢 Green"
    Escreva o **mínimo** de código para o teste passar. Sem elegância ainda; só
    fazer ficar verde.

=== "🔵 Refactor"
    Com a rede de segurança dos testes, **melhore** o código (nomes, duplicação)
    sabendo que, se quebrar, o teste avisa.

!!! quote "O valor do TDD"
    O teste vira **especificação executável**: descreve o que o código deve fazer
    *antes* de ele existir, e continua verificando para sempre.

## Anatomia de um teste (padrão AAA)

Organize cada teste em três blocos: **Arrange, Act, Assert**.

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class CarrinhoTest {

    @Test
    void deveSomarOsPrecosDosItens() {
        // Arrange (preparar)
        var carrinho = new Carrinho();
        carrinho.adicionar(new Item("Café", 10.0));
        carrinho.adicionar(new Item("Pão", 5.0));

        // Act (agir)
        double total = carrinho.total();

        // Assert (verificar)
        assertEquals(15.0, total, 0.001);
    }
}
```

| Assert (JUnit 5) | Verifica |
| :--- | :--- |
| `assertEquals(esp, real)` | valores iguais |
| `assertTrue / assertFalse` | condição booleana |
| `assertThrows(Ex.class, ...)` | que uma exceção é lançada |
| `assertNull / assertNotNull` | nulidade |

## Dublês de teste: mocks

Às vezes a classe depende de algo lento ou externo (banco, API). Usamos um
**dublê** para isolar a unidade sob teste. Com **Mockito**:

```java
import static org.mockito.Mockito.*;

@Test
void deveNegarPedidoSemEstoque() {
    Estoque estoque = mock(Estoque.class);
    when(estoque.disponivel("SKU-1")).thenReturn(false);

    var servico = new PedidoService(estoque);

    assertThrows(SemEstoqueException.class,
        () -> servico.finalizar("SKU-1"));
}
```

!!! warning "Não abuse de mocks"
    Mock demais testa a **interação**, não o **resultado**. Prefira objetos reais
    quando forem rápidos e simples; reserve mocks para dependências externas.

## Boa nomenclatura e independência

!!! tip "Características de um bom teste (F.I.R.S.T.)"
    - **Fast** — roda rápido.
    - **Independent** — não depende da ordem nem de outro teste.
    - **Repeatable** — mesmo resultado sempre.
    - **Self-validating** — passa ou falha, sem conferência manual.
    - **Timely** — escrito junto (ou antes) do código.

## Exercícios

??? abstract "Exercício 1 — Ciclo TDD"
    Descreva, passo a passo, como você usaria Red-Green-Refactor para implementar
    uma função `ehPar(int)`. Escreva o teste **antes** do código.

??? abstract "Exercício 2 — AAA na prática"
    Escreva um teste JUnit no padrão AAA para uma classe `Conta` que não permite
    saque maior que o saldo (deve lançar `SaldoInsuficienteException`).

??? abstract "Exercício 3 — Quando usar mock?"
    Dê um exemplo de dependência que **vale** mockar e um exemplo que **não** vale.
    Justifique com base no F.I.R.S.T.

!!! tip "Próxima Parada 🚀"
    Escreva seus primeiros testes na [**Lista 07 — TDD e Automação**](../listas/07-lista.md).
    Na próxima aula subimos a escada dos **níveis de teste**.
