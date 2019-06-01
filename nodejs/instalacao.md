# Instalar nodejs e npm no CentOS 6x

Para instalar o nodejs e o npm no CentOS 6x siga a instruções abaixo, para a versão escolhida:

## NodeJS 10 (estável)

```
 # Instalando reposiótio
 yum install -y gcc-c++ make
 curl -sL https://rpm.nodesource.com/setup_10.x | sudo -E bash -
 
 # Agora pode ser instalado via o YUM
 yum install nodejs
 
 # Para testar
 node -v 
 v10.*.*
 
 npm -v
 v6.*.*
```
