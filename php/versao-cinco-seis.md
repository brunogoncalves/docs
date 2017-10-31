# Versão 56

Fonte: https://suporte.scriptcase.com.br/pt-br/article/678-configurando-ambiente-manualmente-php-5-6-centos

## Para descobrir a versão atual do PHP:

    yum info php56w
 
## Instalar repositórios no Cenos6x:

    rpm -Uvh https://mirror.webtatic.com/yum/el6/latest.rpm

Verificando a disponibilidade do repositórios recém instalados:

    yum repolist

## Instalando:

Instalando o PHP:

    yum install php56w php56w-mysql php56w-gd php56w-imap php56w-rar php56w-xml php56w-mbstring php56w-cli php56w-common php56w-pecl-imagick php56w-xml php56w-opcache
