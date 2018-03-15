# Exportar coleção para arquivo .json

## Sintaxe:                  
```
mongoexport -d database_name -c collection_name -o outfile.json
```

## Dicas:
- Por padrão o arquivo gerado é .json, não é necessário especificar o tipo

## Exemplo: 
Exportar a coleção Department em myfirstdb database para arquivo json: C:/test/department.json                            
```
mongoexport -d myfirstdb -c Department -o C:/test/department.json
```

![01](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/exportjson01.png)

![02](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/exportjson02.png)

![03](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/exportjson03.png)


