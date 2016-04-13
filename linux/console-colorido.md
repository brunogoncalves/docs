# Console, VIM e Scripts coloridos


- [Para editar o .bashrc](#editar-bashrc)
- [Para o LS já mostrar aberto](#ls-aberto)

<a name="editar-bashrc"></a>
## Para editar o .bashrc

    vim ~/.bashrc

Acrescente as seguintes linhas:

    alias vi='vim'
    export EDITOR='/usr/bin/vim'

<a name="ls-aberto"></a>
## Para o LS já mostrar aberto:

    alias ls='ls -al --color=tty'

