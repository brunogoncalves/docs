# Pacotes

 - [Atualizando pacotes](#atualizando-pacotes)
 - [Instalando o editor VIM](#instalando-vim)
 - [Instalando o SCP](#instalando-scp)
 
 
<a name="atualizando-pacotes"></a>
## Atualizando pacotes
Toda vez que é adquirido um novo cloud ou maquina linux eu costumo sempre atualizar os pacotes da distribuição, executando um `update`

    yum update

<a name="instalando-vim"></a>
## Instalando o VIM
Um bom editor de texto é o VIM, mas algumas instalações não vem com ele instalado, para isso basta executar o comando abaixo:

    yum install vim

<a name="instalando-scp"></a>
## Instando o SCP
O serviço SCP é util para transferir arquivo em máquina linux.

    yum install openssh-clients
