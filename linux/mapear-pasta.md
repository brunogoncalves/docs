# Mapear Pasta compartilhada


Bom, no exemplo abaixo vou mostrar como montar um ponto de disco de uma pasta compartilhada na rede.

Para que nosso exemplo funcione, será utilizado o dispositivo `cifs`

    mount -t cifs //10.10.0.10/pasta_compartilhada /pasta_local

Se precisar informar um usuário e senha no caso de pastar restritas:

    mount -t cifs //10.10.0.10/pasta_compartilhada /pasta_local -o username=usuario,password=senha

