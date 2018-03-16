# Restore de uma base

## Sintaxe:
``` 
mongorestore -d database_name path_to_database
```

## Referências:
[mongorestore](https://docs.mongodb.com/manual/reference/program/mongorestore/index.html)

## Exemplo: 
A pasta C:\test\myfirstdb contém os arquivos de backup. Usaremos ela para restaurar: mydb2                 
``` 
mongorestore -d mydb2 C:\test\myfirstdb
```

![01](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/restore01.png)

![02](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/restore02.png)

![03](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/restore03.png)

