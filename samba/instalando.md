# Instalando

    yum install samba samba-client

Adicione um usuário.

Adicionar usuário no samba:

     smbpasswd -a joao

[global]

        workgroup = BONTUR
        server string = NetForce Bilheteria 32  %v
        netbios name = NETFORCE1
        security = user
        passdb backend = tdbsam
        dns proxy = no
        load printers = no
        cups options = raw


[homes]

        comment = Home Directories
        browseable = no
        writable = yes


[printers]

        comment = All Printers
        path = /var/spool/samba
        browseable = no
        guest ok = no
        writable = no
        printable = no


[install]

        comment = Area comum do Install
        path = /dados/install
        writable = yes
        valid users = netforceinstall,ti
        public = no
        printable = no
        create mask = 0777

