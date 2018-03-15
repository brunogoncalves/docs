#Exportar uma coleção para um arquivo .csv

##Sintaxe:
mongoexport -d database_name -c collection_name -f column_1,column_2,column_3 --csv -o outfile.csv

##Dicas:
- No caso de arquivos csv, você deve informar as lista de colunas da coleção
- a lista de colunas é separada por vifgulas e sem espaços
- Deve-se declarar qual o tipo de arquivo de saida (--csv)

##Examplo: 
Exportar a coleção Department em myfirstdb database para arquivo csv: C:/test/department.csv
mongoexport -d myfirstdb -c Department -f dept_id,dept_no,dept_name,location,description --csv -o C:/test/department.csv
![01](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/exportcsv01.png)
![02](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/exportcsv02.png)
![03](https://raw.githubusercontent.com/brunogoncalves/docs/master/mongodb/imagens/exportcsv03.png)


