# Instalando o PHP

Para instalar o PHP:

    yum install php

Instalando as extensões do PHP:

    yum install php-mysql php-gd php-imap php-rar php-xml php-mbstring

Depois das configurações, o servidor apache deve ser reiniciado.

    service httpd restart

A instalação irá adicionar as configurações do PHP no apache em /etc/httpd/conf.d/php.conf

Neste arquivo costumo mudar/alterar o type

    AddType application/x-httpd-php .php

Dependendo de como é escrito o seu PHP, também costumo aplicar a seguinte alteração no /etc/php.ini

    short_open_tag = On
    register_globals = On

Na versão 5.6 ou superior á um problema com o `CUrl` quando executado via cli funciona mas quando usado via apache não funciona, diz que a função `curl_init()` não existe. Para resolver esse problema é preciso copiar os arquivo abaixo para a pasta bin do apache e reinicia-lo:
 - libeay32.dll
 - libssh2.dll
 - ssleay32.dll
