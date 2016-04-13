# HD Externo

Bom, no exemplo abaixo estou considerando que estou utilizando o servidor `AWS EC2` (da aws.amazom.com) e um volume EBS, no entanto creio que no caso de ser uma máquina local, basta instalar o HD na máquina e fazer o boot reconhecer.

## Montando o HD

Uma vez dentro do linux com o HD externo conectado, podemos verificar se o mesmo está disponível para o linux.

Para verificar se as partições estão disponíveis podemos executar o comando abaixo:

    cat /proc/partitions

Executando o comando a cima, devemos ter algo parecido com isto:

    major minor  #blocks  name
    202        1    8388608 xvda1
    202       32   52428800 xvdc

Neste caso meu HD externo esta na partição xvdc

Para montar basta executar o caminho abaixo

Mas antes você deverá criar o ponto (pasta) onde será montado a partição

     mkdir /dados/

Agora, você deve montar a partição

     mount /dev/xvdc /dados/

Quando o HD estiver zerado, será necessario formatá-lo e atribuir um tipo de fylesystem

Para formar, você poderá executar o comando abaixo:

      mkfs.ext3 /dev/xvdc

## Configurando no boot da máquina
Para fazer a montagem de uma partição de forma automática no boot

Os passos explicados anteriormente devem ser repetidos toda vez que você usar o Linux. Para evitar isso, é possível montar a partição automaticamente, durante o processo de inicialização. Para isso, basta localizar o arquivo fstab.

Geralmente ele se encontra #dentro do diretório /etc/. Abra o arquivo e adicione a seguine linha no final (para o nosso exemplo):

     /dev/xvdc /dados vfat defaults 0 0

[caminho da partição] [ponto de montagem] [tipo] [opções] [ordem]

## Desmontar a partição
Para desmontar uma partição basta executar o comando abaixo:

      umount /dev/xvdc

## Aumentou o tamanho do HD?
Quando for aumentado o tamanho de um HD para o sistema aceitar a expanção deve ser executado o comando abaixo:

     resize2fs /dev/xvdc

