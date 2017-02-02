# Configurando o LESS no PhpStorm

Dentro do PHPStorm, para você configurar seu projeto para operar com LESS, siga as instruções abaixo.

## Passo 1 – Abra seu projeto. 

No exemplo abaixo, vamos considerar que seu projeto tem 2 subdiretórios ```/less``` e ```/css``` onde serão salvos os arquivos ```.less``` e os gerados ```.css```. 

__Importante:__ Caso seus diretórios tenham outro nome, não se esqueça de substituir em todos os passos desse tutorial.

![SettingsPlugins](https://raw.githubusercontent.com/brunogoncalves/docs/master/phpstorm/imgs/print_phpstorm_less_tela1.png)

## Passo 2 – Configurações do Projeto

Clique no menu File e depois em ```Settings...```

![SettingsPlugins](https://raw.githubusercontent.com/brunogoncalves/docs/master/phpstorm/imgs/print_phpstorm_less_tela2.png)

## Passo 3 – Arquivos de Disparos

Abrirá uma janela igual a imagem abaixo. Nessa janela, na barra esquerda, clica em ```Tools``` e depois em File Watches.
Com o espaço que abrirá ao lado da barra que você clicou, clica no ícone verde com o ```+``` e depois em LESS.
  
![SettingsPlugins](https://raw.githubusercontent.com/brunogoncalves/docs/master/phpstorm/imgs/print_phpstorm_less_tela3.png)

##Passo 4 - Configurações do LESS
Abrirá uma caixa onde você configurará a compilação do seu arquivo LESS. 
No campo ```Arguments``` você configura os parâmetros do aplicativo do LESS. 
No exemplo utilizado na imagem abaixo, consideramos que entro do diretório ```/less``` existe um arquivo chamado ```script.less```. 
No campo ```Output paths``` ro reference você especifica qual o diretório e arquivo que será salvo o arquivo compilado. 
No nosso exemplo abaixo, ```css/style.css```.

![SettingsPlugins](https://raw.githubusercontent.com/brunogoncalves/docs/master/phpstorm/imgs/print_phpstorm_less_tela3.png)

## Passo 5 - Pronto!

Seu sistema já está configurado. Toda vez que você salvar um arquivo do seu projeto, será executado o comando que compila seu arquivo LESS.
