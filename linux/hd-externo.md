# HD Externo

Bom no exemplo abaixo eu estou considerando que estou utilizando o servidor AWS EC2 (da aws.amazom.com) e um volume EBS, no entanto creio que no caso de ser uma máquina local, basta instalar o HD na maquina e fazer o boot reconhecer.

Uma vez dentro do linux com o HD externo conectado, podemos verificar se o mesmo está disponível para o linux.

Para verificar se as partições estão disponíveis podemos executar o comando abaixo:

    cat /proc/partitions

v hhvhvhg:

    major minor  #blocks  name
    202        1    8388608 xvda1
    202       32   52428800 xvdc

Neste caso meu HD externo esta na partição xvdc
