# Aula 01 — Introdução

!!! info "Objetivos da aula"
    - Entender o que é documentação técnica e por que ela importa.
    - Conhecer o MkDocs e o tema Material.
    - Rodar o site localmente pela primeira vez.

## O que vamos usar

Este material é escrito em **Markdown** e publicado com **MkDocs Material**, o mesmo padrão usado por projetos de mercado para documentação.

=== "Markdown"
    ```markdown
    # Título
    Texto com **negrito** e *itálico*.

    - item de lista
    - outro item
    ```

=== "Resultado"
    Um site navegável, com busca, modo escuro e menu lateral — gerado automaticamente a partir dos arquivos `.md`.

## Rodando localmente

Com o ambiente já configurado (veja o [Guia do Professor](../setup.md)):

```bash
mkdocs serve
```

Acesse `http://127.0.0.1:8000`. O site recarrega sozinho a cada vez que você salva um arquivo.

!!! tip "Dica"
    Deixe o `mkdocs serve` rodando em um terminal enquanto edita. Assim você vê as mudanças em tempo real.

## Para a próxima aula

??? abstract "Checklist"
    - [ ] Ambiente virtual criado e ativado
    - [ ] `pip install -r requirements.txt` executado
    - [ ] Site abrindo em `http://127.0.0.1:8000`

!!! warning "Atenção"
    Blocos como este (admonitions) exigem **recuo de 4 espaços** no conteúdo. Se o texto "vazar" para fora da caixa, confira a indentação.
