# Alterando o diretório padrão do Bower

Por padrão, o diretório que o Bower utiliza pra salvar os pacotes instalados é ```bower_components/```. 
Caso você queira modificar, basta criar um arquivo chamado ```.bowerrc``` com o seguinte conteúdo:

    {
	    "directory":"assets/components"
    }

**Observação:***
Depois de alterar o diretório dos pacotes, remova o diretório anterior - ```bower_componentes``` - e execute o ```bower install```, pra ele fazer download das dependências novamente.
