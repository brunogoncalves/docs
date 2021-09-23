# Fazendo o Rebase ou Merge de forks

Quando você tem um fork de um outro repositório e precisa fazer o rebase e/ou merge, trazendo as atualizações do repositorio principal para o seu fork, pode ser 
feito da seguinte forma:

```bash
# Adicione um novo remote; pode chamá-lo de "oficial":

git remote add oficial https://github.com/usuario_original/repositorio_original.git

# Obtenha todos os branches deste novo remote,
# como o oficial/main por exemplo:

git fetch oficial

# Certifique-se de que você está no branch main:

git checkout main

# Reescreva o seu branch main, de forma que os seus commits
# que não estão no projeto original apareçam, e que os seus
# commits fiquem no topo da lista:

# Para fazer o rebase
git rebase oficial/main

# ou Para fazer o merge somente
git merge oficial/main

# No entanto, para fazer com que futuros pull requests fiquem o mais
# limpos possível, é uma boa ideia fazer o rebase.

# Se você fez o rebase do seu branch a partir de oficial/main, talvez
# você precise forçar um push para o seu próprio repositório do Github.
# Você pode fazer isso com:

git push -f origin main
```
