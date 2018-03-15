# Importar arquivo .json para coleção

## Sintaxe:
```
mongoimport -d database_name -c collection_name outfile.json
```

## Dicas:

## Exemplo: 
Importar para myfirstdb database a coleção Department2 do arquivo C:/test/department.json                
```
mongoimport -d myfirstdb -c Department2 C:/test/department.json
```

![01](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/importjson01.png)

![02](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/importjson02.png)

![03](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/importjson03.png)


