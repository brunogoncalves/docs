# Data, hora e fuso

Listar zonas de fusos:

    ls /usr/share/zoneinfo/America/

Alterar o fuso atual:

    ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime

Para usar o passo-a-passo:

    tzselect

Alterar data e hora:

    date mmddhhmmyyyy 

O significado de cada conjunto de caracteres é:

mm: mês

dd: dia

hh: hora

mm: minuto

yyyy: ano

Depois de digitado o comando com os respectivos valores, digite o código a seguir para salvar as alterações: 

    clock -w 

Outra maneira de fazer a alteração:

    [http://www.opcaolinux.com.br/gnulinux/dicas/14-comandos-linux/31-como-ajustar-a-data-e-a-hora-de-um-servidor-linux.html]

    hwclock --set --date "12/22/2007 22:00:00"
    hwclock --hctosys

O primeiro comando ajustou o relógio do hardware (placa mãe) e o segundo sincronizou esse relógio com o relógio do sistema operacional.
