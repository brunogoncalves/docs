# Criando uma liberação no GitHub (Tag)

Para executar uma liberação via linha de comando, basta executar os comandos abaixo:

    # Criar a liberação no repositorio local
    git tag -a 1.0.0 -m "Aki vai o comentario"

    # Enviar a liberação para o github
    git push --tags

Para excluir um tag, basta executar o comando abaixo:

```bash
# O id da tag neste exemplo é v1.0.0
git tag -d v1.0.0
git push origin :refs/tags/v1.0.0
```