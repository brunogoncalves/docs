# Autenticação

Para ativar a autenticação do mongodb, primeiro deve ser inciado o mongo com o controle de autenticação 
desligado para o mesmo poder ser configurado.

Em /etc/mongod.conf:
```
#security:
#    authorization: enabled
```

Com o mongo inicado agora, entre no console `mongo` e digite as informações abaixo:

```
use admin

db.createUser({user:"root", pwd:"1234", roles:[...], mechanisms:["SCRAM-SHA-1"]})
```

Sendo que as ``roles`` devem ser:

```
{
   "roles" : [ 
        {
            "role" : "read",
            "db" : "admin"
        }, 
        {
            "role" : "readWrite",
            "db" : "admin"
        }, 
        {
            "role" : "dbAdmin",
            "db" : "admin"
        }, 
        {
            "role" : "userAdmin",
            "db" : "admin"
        }, 
        {
            "role" : "readAnyDatabase",
            "db" : "admin"
        }, 
        {
            "role" : "readWriteAnyDatabase",
            "db" : "admin"
        }, 
        {
            "role" : "userAdminAnyDatabase",
            "db" : "admin"
        }, 
        {
            "role" : "dbAdminAnyDatabase",
            "db" : "admin"
        }
    ]
 }
```

Após isso deve ser configurado o mongod para iniciar com a estrutura de autenticação habilitada e pronto
