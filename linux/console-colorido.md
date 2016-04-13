# Console, vim e Scripts coloridos

Para definir as cores dos scripts iremos adicionar algumas definições no arquivo `.bashrc`

Abra o arquivo executando o comando abaixo:

    vim ~/.bashrc

Defina o editor `vim` como editor padrão adicionando as linhas abaixo:

    alias vi='vim'
    export EDITOR='/usr/bin/vim'

Defina que o comando `ls` sempre exiba todas as informações e colorido, adicionando a linha abaixo:

    alias ls='ls -al --color=tty'

