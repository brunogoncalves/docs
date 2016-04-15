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
