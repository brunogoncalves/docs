# Adicionando pacote no Bower

Como de costume na maioria dos projetos *front-end*, vamos utilizar o ```JQuery``` como dependência. 
Vou mostrar duas maneiras de adicioná-lo ao seu projeto utilizando o Bower.

## Maneira 1 - Com comando
Execute o camando ```bower install <package>```

No caso do jQuery, seria assim:

    bower install jquery --save
  
**Observação:** 
A opção ```--save``` serve para adicionar o pacote no ```dependencies``` do ```bower.json```.

## Maneira 2 - Manualmente
Abre e edite o arquivo ```bower.json``` adicionando:

         ...
	    "ignore": [
    		"**/.*",
    		"node_modules",
    		"bower_components",
    		"test",
    		"tests"
	    ]
            "dependencies": {
                    "jquery": "~2.0.3"
            }
    }

e em seguida executar:

    bower install
    
**Obersação:**
Toda vez que você executa o ```bower install```, ele verifica quais as dependências existentes no seu arquivo ```bower.json``` e caso elas não estejam presentes na pasta de componentes serão instaladas.

