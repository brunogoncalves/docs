# Instalando

Instalando o servidor de FTP:

    yum install vsftpd

 Para configurar o VsFTP:

    vim /etc/vsftpd.conf

Vamos desabilitar o acesso anônimo.

    anonymous_enable=NO

Para permitir o acesso a utilizadores locais:

    local_enable=YES

Exibir mensagem no login:

    ftpd_banner=Bem Vindo ao FTP

Não permitir que o usuário via FTP saia navegando em outras pastas do sistema:

    chroot_local_user=YES

Configuração para Pasive Mode:

Lembrando que a porta 10000 ou faixa de portas informado abaixo deve ser liberado no firewall.

    pasv_enable=YES
    pasv_min_port=10000
    pasv_max_port=10100
    pasv_promiscuous=YES

Permitir que seja exibido os arquivo .htacess

    force_dot_files=YES

Antes de começar a criar o usuário para acessar o ftp, vamos configurar o shell/false.

    vim /etc/shells

Adicione o /bin/false na lista se não tiver.

Para criar um usuário:

    useradd usuario -d /dados/www/ -s /bin/false -N

Adicionando o usuário criado ao grupo root:

   gpasswd -a usuario root

Definindo uma senha para o usuário:

    passwd usuario

Definir propriedade sobre a pasta "home":

    chown usuario:root /dados/www

ATENÇÃO: SELINUX

Em alguns casos foi necessário desativar o selinux, onde isso pode ser feito da seguinte forma:

Edite o arquivo vim /etc/sysconfig/selinux desativando o campo SELINUX informando o valor para SELINUX=disabled

`É EXTREMAMENTE IMPORTANTE REINICIAR O SERVIDOR`
