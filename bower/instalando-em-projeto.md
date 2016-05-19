# Instalando Bower num projeto

Nesse exemplo, vamos ilustrar um projeto web simples, sem *back-end*, mas garanto que vai ficar fácil de entender como incorpora-lo ao seu projeto, independente da linguagem.

Nosso projeto vai se chamar ```zombie-striker``` e terá a seguinte estrutura:

    |zombie-striker/
    |--assets/
    |----scripts/
    |----styles/
    |----images/
    |--index.html

Para adicionarmos o Bower, vamos até a pasta do projeto ```/zombie-striker``` e digitar o comando:

    bower init

O Bower irá iniciar um *wizard* para gerar o arquivo ```bower.json``` pedindo pra você completar as seguintes informações:

    # nome do projeto
    name:zombie-striker 
 
    # versão do projeto
    version:0.0.1
 
    # descrição do projeto
    description: app to strike zombies with bower
 
    # arquivo principal do seu projeto
    main file: assets/scripts/main.js
 
    # palavras-chaves 
    keywords: zombie striker
 
    # autores do projeto
    authors: "Tihh Gonçalves <tiago@tiago.art.br>"
 
    # tipo de licença
    license: MIT
 
    #homepage do projeto
    homepage: "https://github.com/diRex/zombie-striker"
 
    # se você gostaria que o bower adicionasse os components já instalados, como dependências no arquivo json.
    set currently installed components as dependencies?(y/n) n
 
    # se você gostaria de adicionar o ignore list default do bower
    add commonly ignored files to ignore list?(y/n) y
 
    # se você gostaria de tornar esse pacote privado para que não seja acidentalmente publicado no registro de pacotes do bower.
    would you like to mark this package as private which prevents it from beig accidentally published to the registry?(y/n) y

*Observação:* 

Algumas das opções acimas são válidas apenas para pacotes que vão ser distribuídos como novos componentes, por exemplo: caso você esteja criando um novo framework e queira disponibilizar aos demais através do bower. 

Porém, não é nosso caso, então podemos utilizar o ```bower.json``` gerado pelo *wizard* e modificar de acordo com a nossa necessidade. Caso você queira, pode pular a etapa de *wizard* do ```bower init``` e  criar o ```bower.json``` na mão com as opções que você queira.

    {
    	"name": "zombie-striker",
    	"version": "0.0.1",
    	"authors": [
    		"Diogo Vecchiati <http://divecch.com>"
    	],
    	"description": "app to strike zombies with bower",
    	"main": "assets/scripts/main.js",
    	"keywords": [
    		"zombie"
    	],
    	"license": "MIT",
    	"homepage": "https://github.com/diRex/zombie-striker",
    	"private": true,
    	"ignore": [
    		"**/.*",
    		"node_modules",
    		"bower_components",
    		"test",
    		"tests"
    	]
    }
