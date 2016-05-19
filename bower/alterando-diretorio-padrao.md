# Alterando o diretório padrão do BOWER

Por padrão, o diretório que o BOWER utiliza pra salvar os componentes instalados é ```bower_components/```. 
Caso você queira modificar, basta criar um arquivo chamado ```.bowerrc``` com o seguinte conteúdo:

    {
	    "directory":"assets/components"
    }

**Observação:***
Depois de alterar o diretório dos componentes, remova o diretório anterior, ```bower_componentes``` e execute o ```bower install```, pra ele fazer download das dependências novamente.
