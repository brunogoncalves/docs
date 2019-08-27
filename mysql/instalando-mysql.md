# Para versão 5.7

    sudo yum install https://dev.mysql.com/get/mysql-community-common-5.7.27-1.el6.x86_64.rpm
    
    sudo yum install https://dev.mysql.com/get/mysql-community-libs-5.7.27-1.el6.x86_64.rpm
    
    sudo yum install https://dev.mysql.com/get/mysql-community-client-5.7.27-1.el6.x86_64.rpm
    
    sudo yum install https://dev.mysql.com/get/mysql-community-server-5.7.27-1.el6.x86_64.rpm
    
    # Desde a versão 5.6 o mysql gera um senha temporaria, para pega-la execute
    
    sudo cat /var/log/mysqld.log | grep 'temporary password'

# Instalando

Para instalar o servidor MySQL execute o comando abaixo:

    yum install mysql mysql-server

Para iniciar o MySQL basta executar:

    service mysqld start

Neste ponto, costumo alterar a pasta de dados do MySQL para o HD externo.

Então com o MySQL parado (service mysqld stop) podemos mudar seguindo os passos abaixo:


Copiando a pasta MySQL para o HD externo:

    cp -r -p /var/lib/mysql/ /dados/mysql/

Renomeie a pasta antiga do MySQL para que você tenha um backup. Depois verifique se o MySQL funciona no novo local:

    mv /var/lib/mysql /var/lib/mysql.bkp/

Agora você precisa criar um link simbólico para o MySQL no local antigo para apontar para o novo caminho.

    ln -s /dados/mysql/ /var/lib/mysql

Inclua ou altere o caminho do novo local do arquivo /etc/my.cnf

    datadir=/dados/mysql/

Agora o MySQL já pode ser iniciado.

    service mysqld start

Agora você deverá atribuir as permissões e acessos ao usuário root.

Para isso entre no MySQL com o usuário root.

    mysql -u root

Vamos atribuir uma senha para o usuário root e liberar acesso externo.

    GRANT ALL ON *.* TO `root`@`%` IDENTIFIED BY ‘sua_senha’;
    GRANT ALL ON *.* TO `root`@`localhost` IDENTIFIED BY ‘sua_senha’;
    FLUSH PRIVILEGES;

## Windows

Nas instalações no Windows, geralmente é incluído no my.ini a diretiva abaixo:

No arquivo my.ini no diretório da instalação do MySQL essa diretiva permite que o nome da tabelas sejam informado em letras maiúsculas.

    lower_case_table_names=0

Uma outra configuração que preciso fazer para o DataBuilder via ODBC MySQL é no BDE aumentar o campo BLOBS TO CACHE

No BDE em: Configurations \ Drivers \ ODBC \ MySQL ODBC 3.51 Driver

## Erros

Em máquinas replicadas quando vai ser importando um SCRIPT com alteração de banco ocorre o seguinte erro: binary logging not possible

Para corrigir esse problema deve ser carregado um SQL Query e executar o seguinte comando:

SET GLOBAL binlog_format = 'ROW';

## Tabelas em arquivos separados

Para configurar que cada tabela esteja em um arquivo separado no InnoDB, você deve ativar essa funcionalidade no my.cnf

    innodb_file_per_table = 1
    
    
