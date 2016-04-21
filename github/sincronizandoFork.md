# Sincronizando o Fork

Abra o git bash ou qualquer outro console no projeto:

![GitBash](https://raw.githubusercontent.com/JohannLucas/docs/master/github/imgs/printGitBash.jpg)

## Caso já tenha criado o Upstream

Execute os seguintes comandos no console:

    git fetch upstream
    
    git merge upstream/master master
    
    git rebase upstream/master


## Caso contrário

Execute o seguintes comandos no console:

    git remote add upstream git://github.com/usuario/repositorio.git
    
    git fetch upstream
    
    git merge upstream/master master
    
    git rebase upstream/master




