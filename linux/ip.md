# Configurando IP na máquina

A instalação `default` configura como a rede como DHCP e para tornalo estático precisamos alterar alguns arquivos que foi osso lembrar.

## Definindo o IP Estático
Logado como root edite o arquivo: `vim /etc/sysconfig/network-scripts/ifcfg-eth0`

```bash
ONBOOT=yes
BOOTPROTO=static
IPADDR=192.168.1.100
NETMASK=255.255.255.0
```

## Configurando o Gateway
Edite o arquivo: `vim  /etc/sysconfig/network`

```bash
GATEWAY=192.168.1.1
```

## Configurando os DNSs
Edite o arquivo `/etc/resolv.conf` 

```bash
# DNS do Google
nameserver 8.8.8.8
nameserver 8.8.4.4
```

## Aplicando alterações
Após fazer as alterações necessárias é preciso reiniciar o serviço de rede:

```bash
service network restart
```
