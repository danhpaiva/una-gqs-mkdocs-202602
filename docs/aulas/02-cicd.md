# Aula 02 — CI/CD com GitHub Actions

!!! info "Objetivos da aula"
    - Entender o que é CI/CD e por que automatizar a publicação.
    - Conhecer o workflow do GitHub Actions deste template.
    - Publicar o site automaticamente no GitHub Pages.

## O que é CI/CD

**CI/CD** (Integração e Entrega Contínuas) é a prática de automatizar as etapas entre escrever o conteúdo e publicá-lo. Neste template, a cada `push` na branch `main`, o site é construído e publicado sem nenhum passo manual.

## O workflow deste template

O arquivo `.github/workflows/ci.yml` define dois trabalhos:

=== "build"
    Instala as dependências e executa `mkdocs build --strict`, que **falha** se houver link interno quebrado. Roda em `main` e `develop`.

=== "deploy"
    Publica o resultado no GitHub Pages. Roda **apenas na `main`**, para não sobrescrever a produção a partir de branches de trabalho.

!!! tip "Dica"
    Use a `develop` para escrever e revisar: o build valida seu conteúdo sem publicar. Quando estiver pronto, leve para a `main`.

## Publicando

1. Configure o Pages e as permissões (veja o [Guia do Professor](../setup.md)).
2. Faça `push` na branch `main`.
3. Acompanhe a execução na aba **Actions** do GitHub.

!!! warning "Exercício 1"
    Faça uma alteração em qualquer página, publique pela `main` e confirme que o site atualizou. Anote a URL do seu Pages para a entrega do [Projeto 01](../trabalhos/projeto-01.md).
