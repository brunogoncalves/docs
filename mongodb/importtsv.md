# Importar arquivo .txt para coleção

## Sintaxe:
``` 
mongoimport -d database_name -c collection_name --type tsv --fields col1,col2,col3 --file locations.txt --headerline
```

## Dicas:
--headerline: Ignora a primeira linha do arquivo onde estão os nomes das colunas da coleção.

## Referências:
[mongoimport](https://docs.mongodb.com/manual/reference/program/mongoimport/index.html#use)

## Exemplo: 
Importar para myfirstdb database a coleção Department3 do arquivo C:/test/department.txt                             
``` 
mongoimport -d myfirstdb -c Department3 --type tsv --fields coluna1, coluna2,coluna3--file C:/test/department.txt --headerline
```



