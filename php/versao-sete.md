# Versão 70

Fonte: https://webtatic.com/packages/php71/

Para install PHP72 no centos6 https://www.tecmint.com/install-php-7-in-centos-6/ (testei no docker)

## Para descobrir a versão atual do PHP:

    yum info php70w
 
## Instalar repositórios no Cenos6x:

    yum install epel-release
    rpm -Uvh https://mirror.webtatic.com/yum/el6/latest.rpm
    
## Instalar repositórios no Cenos7x:

    yum install epel-release
    rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm    

Verificando a disponibilidade do repositórios recém instalados:

    yum repolist

## Instalando:

Instalando o PHP:

    yum install php70w php70w-mysql php70w-gd php70w-imap php70w-rar php70w-xml php70w-mbstring php70w-cli php70w-common php70w-pecl-imagick php70w-xml php70w-opcache
