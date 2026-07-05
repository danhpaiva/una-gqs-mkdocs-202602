# 🧪 Garantia e Qualidade de Software

Bem-vindo(a)! Aqui você encontra o material de apoio, o cronograma e as listas de
exercícios da disciplina **Garantia e Qualidade de Software (GQS)** — 2026/2.

!!! info "Objetivo da Disciplina"
    Formar o estudante para **planejar, executar e automatizar** atividades de
    garantia da qualidade de software. Ao final, você será capaz de aplicar
    técnicas de revisão e teste (caixa branca e preta), escrever testes
    automatizados com TDD, medir software com métricas e pontos de função, e
    reconhecer modelos de qualidade de processo (ISO, CMMI e MPS.BR) em um fluxo
    moderno de **DevOps e Integração Contínua**.

## 🎯 O que você vai dominar

=== "🧑‍🔬 Qualidade & Testes"
    - Conceitos de qualidade de produto e de processo.
    - Revisão, inspeção e garantia da qualidade (QA).
    - Testes de caixa branca e caixa preta.
    - Níveis de teste: unitário, integração, sistema e validação.
    - TDD e testes automatizados.

=== "📈 Medição & Processo"
    - Medidas, métricas e indicadores.
    - Pontos de função e estimativa de projetos.
    - Modelos de qualidade: ISO 9126, CMMI e MPS.BR.
    - Gestão de configuração e controle de versão.
    - Manutenção, reengenharia e melhoria de processo.

=== "⚙️ Prática (Java)"
    ```java
    import static org.junit.jupiter.api.Assertions.assertEquals;
    import org.junit.jupiter.api.Test;

    class CalculadoraTest {
        @Test
        void deveSomarDoisNumeros() {
            var calc = new Calculadora();
            assertEquals(4, calc.somar(2, 2));
        }
    }
    ```
    Os exemplos de teste da disciplina usam **Java + JUnit 5** (com Mockito
    quando precisarmos de dublês de teste).

## 🗓️ Cronograma

| Aula | Assunto | Entrega |
| :--- | :--- | :--- |
| [01](aulas/01-aula.md) | Qualidade de Software e Garantia da Qualidade (QA) | [Lista 01](listas/01-lista.md) |
| [02](aulas/02-aula.md) | DevOps e Integração Contínua (CI/CD) | [Lista 02](listas/02-lista.md) |
| [03](aulas/03-aula.md) | Técnicas de Revisão e Inspeção de Software | [Lista 03](listas/03-lista.md) |
| [04](aulas/04-aula.md) | Fundamentos e Estratégias de Teste | [Lista 04](listas/04-lista.md) |
| [05](aulas/05-aula.md) | Teste de Caixa Branca (Estrutural) | [Lista 05](listas/05-lista.md) |
| [06](aulas/06-aula.md) | Teste de Caixa Preta (Funcional) | [Lista 06](listas/06-lista.md) |
| [07](aulas/07-aula.md) | TDD e Testes Automatizados | [Lista 07](listas/07-lista.md) |
| [08](aulas/08-aula.md) | Níveis de Teste: Unitário ao Sistema | [Lista 08](listas/08-lista.md) |
| [09](aulas/09-aula.md) | Plano e Roteiro de Testes | [Lista 09](listas/09-lista.md) |
| [10](aulas/10-aula.md) | Métricas, Indicadores e Pontos de Função | [Lista 10](listas/10-lista.md) |
| [11](aulas/11-aula.md) | Modelos de Qualidade: ISO, CMMI e MPS.BR | [Lista 11](listas/11-lista.md) |
| [12](aulas/12-aula.md) | Gestão de Configuração, Manutenção e Reengenharia | [Lista 12](listas/12-lista.md) |

!!! note "Trabalho final"
    O trabalho integrador da disciplina será divulgado ao longo do semestre.
    Fique de olho nos avisos do Google Classroom.

## 🧰 Ferramentas

Antes das atividades práticas, confira a página de [🧰 Ferramentas](ferramentas.md)
e deixe seu ambiente pronto (JDK, VS Code, Git). O fluxo de entrega das listas usa
**Git + GitHub** — cada lista vira um repositório público seu.

## 💡 Dicas de estudo

??? tip "Como aproveitar melhor cada aula"
    - **Leia antes da aula:** chegue com as dúvidas anotadas.
    - **Reproduza os exemplos:** copiar e rodar o código fixa o conteúdo.
    - **Faça a lista no mesmo dia:** o assunto ainda está fresco.
    - **Use o Git desde o início:** commits pequenos e frequentes contam história.

!!! danger "Atenção com Prazos"
    As listas têm prazo no Google Classroom. Entregas atrasadas podem não ser
    aceitas pelo sistema — não deixe para o último dia.
