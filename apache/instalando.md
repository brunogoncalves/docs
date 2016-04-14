# Instalando

Para instalar o apache:

    yum install httpd

Marcando o httpd/apache para inicializar no boot da máquina:

    chkconfig httpd on

Caso não esteja adicionado ainda, pode ser incluido na lista:

    chkconfig -add httpd

Para inicializar o apache:

    service httpd start

Configurações do HTTPd fica em:

    cd /etc/httpd/conf/
    cd /etc/httpd/conf.d/
