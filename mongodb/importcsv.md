# Importar arquivo .csv para coleção

## Sintaxe:
``` 
mongoimport -d database_name -c collection_name --type csv --file locations.csv --headerline
```

## Dicas:
--headerline: Usa a primeira linha do arquivo para o nome das colunas da coleção.

## Exemplo: 
Importar para myfirstdb database a coleção Department3 do arquivo C:/test/department.csv                             
```
mongoimport -d myfirstdb -c Department3 --type csv --file C:/test/department.csv --headerline
```

![01](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/importcsv01.png)

![02](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/importcsv02.png)

![03](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/importcsv03.png)



