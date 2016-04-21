# Versão 54

## Para descobrir a versão atual do PHP:

    yum info php
 
    Loaded plugins: fastestmirror
    Loading mirror speeds from cached hostfile
    * base: mirrors.sin3.sg.voxel.net
    * extras: mirrors.sin3.sg.voxel.net
    * updates: mirror.neu.edu.cn
    Available Packages
    Name        : php
    Arch        : x86_64
    Version     : 5.3.3
    Release     : 23.el6_4
    Size        : 1.1 M
    Repo        : updates
    Summary     : PHP scripting language for creating dynamic web sites
    URL         : http://www.php.net/
    License     : PHP
    Description : PHP is an HTML-embedded scripting language. PHP attempts to make it
            : easy for developers to write dynamically generated webpages. PHP also
            : offers built-in database integration for several commercial and
            : non-commercial database management systems, so writing a
            : database-enabled webpage with PHP is fairly simple. The most common
            : use of PHP coding is probably as a replacement for CGI scripts.
            :
            : The php package contains the module which adds support for the PHP
            : language to Apache HTTP Server.

## Instalar repositórios:

Iremos adicionar os repositórios, que são:

1. epel
2. remi
3. rpmforge

Você irá precisar ter permissões de administrador (sudo ou su)

CentOS - Carregando o repositório EPEL

    rpm -Uvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm

CentOS - Carregando o repositório REMI

    rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm

CentOS - Carregando o repositório RPMFORGE
 
    rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm

Verificando a disponibilidade do repositórios recém instalados:

    yum repolist

## Configurando os repositórios:

Esse repositório não é suportado pelo CentOS, então para dependências, só habilite quando você quiser um pacote especial.

    vi /etc/yum.repos.d/epel.repo
    /etc/yum.repos.d/epel.repo
    [epel]
    name=Extra Packages for Enterprise Linux 6 - $basearch
    #baseurl=http://download.fedoraproject.org/pub/epel/6/$basearch
    mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=epel-6&arch=$basearch
    failovermethod=priority
    enabled=0 # 1 -> 0 disable
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6
    

    vim /etc/yum.repos.d/rpmforge.repo
    /etc/yum.repos.d/rpmforge.repo
    [rpmforge]
    name = RHEL $releasever - RPMforge.net - dag
    baseurl = http://apt.sw.be/redhat/el6/en/$basearch/rpmforge
    mirrorlist = http://mirrorlist.repoforge.org/el6/mirrors-rpmforge
    #mirrorlist = file:///etc/yum.repos.d/mirrors-rpmforge
    enabled = 0 # 1 -> 0
    protect = 0
    gpgkey = file:///etc/pki/rpm-gpg/RPM-GPG-KEY-rpmforge-dag
    gpgcheck = 1

Configurá-los explicitamente com opção, você pode usar para tentar obter informações sobre php

Chegar disponibilidades:

    yum --enablerepo=epel,remi,rpmforge info php
 
    Name        : php
    Arch        : x86_64
    Version     : 5.4.22
    Release     : 1.el6.remi
    Size        : 2.7 M
    Repo        : remi
    Summary     : PHP scripting language for creating dynamic web sites
    URL         : http://www.php.net/
    License     : PHP and Zend and BSD
    Description : PHP is an HTML-embedded scripting language. PHP attempts to make it
                : easy for developers to write dynamically generated web pages. PHP also
                : offers built-in database integration for several commercial and
                : non-commercial database management systems, so writing a
                : database-enabled webpage with PHP is fairly simple. The most common
                : use of PHP coding is probably as a replacement for CGI scripts.
                :
                : The php package contains the module (often referred to as mod_php)
                : which adds support for the PHP language to Apache HTTP Server.

## Instalando:

Instalando o PHP:

    yum --enablerepo=epel,remi,rpmforge install php php-mysql php-gd php-imap php-rar php-xml php-mbstring

Instalando o MySQL:

    yum --enablerepo=epel,remi,rpmforge install mysql-server mysql-devel
