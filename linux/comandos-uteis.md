# Outros comandos úteis

Criar/editar tarefas da cron de outro usuário

    crontab -u netforce -e

Descobrir o tamanho de uma pasta:

    du -hs /netforce/

Descobrir o tamanho das partições:

    df -h

Exibir informações de CPU:

    cat /proc/cpuinfo

Exibir o uso da memória:

Exibir pela unidade Mb:

    free -m

Exibir tabela completa:

    vmstat

Informações completas:

    cat /proc/cpuinfo 

Limpar cache:

    sync ; echo 3 > /proc/sys/vm/drop_caches

Exibir informações sobre os serviços:

Exibir a lista completa de todos os serviços:

    service --status-all
 
Exibir informação de um serviço específico:

    service --status-all | grep mysqld
 
Lista os serviços com portal abertas:

    netstat -tulpn

Sendmail:

SendMail do Linux:
 
As mensagens a ser enviadas estão na pasta:

    /var/spool/mqueue/
 
Para ver a lsita de mensages:

    mailq

Listar usuários já registrados:

    getent passwd | cut -d \: -f1

