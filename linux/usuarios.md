# Usuários



Para criar usuários que não irão fazer login no sistema (ssh) mas será utilizado no APACHE e FTP

Devemos associá-los ao shell/false

## Para configurar o shell/false:

    vim /etc/shells

Adicione o `/bin/false` na lista se não tiver

## Para criar um usuário:

    useradd usuario -d /dados/www/ -s /bin/false -N

## Adicionando o usuário criado ao grupo root:

    gpasswd -a usuario root

## Definindo uma senha para o usuário:

    passwd usuario

## Definir propriedade sobre a pasta "home":

    chown usuario:root /dados/www

## Desativando a necessidade de acesso via certificado

https://www.liberiangeek.net/2014/07/enable-ssh-key-logon-disable-password-password-less-logon-centos/
