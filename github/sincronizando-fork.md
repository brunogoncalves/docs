# Sincronizando o Fork

Abra o GitBash ou qualquer outro console no projeto:

![GitBash](https://raw.githubusercontent.com/brunogoncalves/docs/master/github/imgs/print-gitbash.jpg)

## Caso já tenha criado o Upstream

Execute os seguintes comandos no console:

    git fetch upstream
    
    git merge upstream/master master
    
    git rebase upstream/master
    
## Caso contrário

Execute os seguintes comandos:

    git remote add upstream git://github.com/usuario/repositorio.git
    
    git fetch upstream
    
    git merge upstream/master master
    
    git rebase upstream/master
    
    
