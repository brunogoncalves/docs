# Sincronizando o Fork

Abra o GitBash ou qualquer outro console no projeto:

![GitBash](https://raw.githubusercontent.com/brunogoncalves/docs/master/github/imgs/print-gitbash.jpg)

## Verificar se já possui o Upstream    

Para sincronizar o fork você precisa saber se já possui um Upstream criado no remote, para isso execute o comando que irá listar o remote:

     git remote -v
     
Se você não possuir upstreams você terá o seguinte resultado:

![GitBash-NoHaveUpstream](https://raw.githubusercontent.com/brunogoncalves/docs/master/github/imgs/github-remote-origin.jpg)

Já se você possuir terá esse resultado:

![GitBash-HaveUpstream](https://raw.githubusercontent.com/brunogoncalves/docs/master/github/imgs/github-remote-upstream.jpg)

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
    
```blob 
Caso o repositório de origem for privado bote sua url da seguinte maneira:
git@github.com:usuario/repositorio.git
```

## Remover Upstream

Execute o seguinte comando para remover os upstreams:

     git remote rm upstream
