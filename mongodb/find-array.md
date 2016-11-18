# Find - Array

Supondo que temos uma coleção chamada __Pessoas__ e nela temos os seguintes registros:

```json
	{ 
		"_id" : ObjectId("582deedf7099709a17b8314b"), 
		"nome" : "Johann", 
		"sobrenome" : "Lucas", 
		"idade" : 17, 
		"sexo" : "Masculino", 
		"profissao" : "Programador", 
		"habilidades" : [
			{
				"nome" : "Inglês", 
				"nivel" : "Intermediário"
			}
		]
	}
	{ 
		"_id" : ObjectId("582df06b7099709a17b8314c"), 
		"nome" : "Thaís", 
		"sobrenome" : "Meester", 
		"idade" : 16, 
		"sexo" : "Feminino", 
		"profissao" : "NA", 
		"habilidades" : [
			{
				"nome" : "Ingles", 
				"nivel" : "Avançado"
			}
		]
	}
	{ 
		"_id" : ObjectId("582df14e7099709a17b8314d"), 
		"nome" : "Jean", 
		"sobrenome" : "Patrick", 
		"idade" : 21, 
		"sexo" : "Masculino", 
		"profissao" : "Programador C#", 
		"habilidades" : [
			{
				"nome" : "Ingles", 
				"nivel" : "Avançado"
			}
		]
	}
	{ 
		"_id" : ObjectId("582df14e7099709a17b8314e"), 
		"nome" : "Bruno", 
		"sobrenome" : "Gonçalves", 
		"idade" : 32, 
		"sexo" : "Masculino", 
		"profissao" : "Businessman", 
		"habilidades" : [
			{
				"nome" : "Laravel Framework", 
				"nivel" : "Avançado"
			}
		]
	}
	{ 
		"_id" : ObjectId("582df14e7099709a17b8314f"), 
		"nome" : "Matheus", 
		"sobrenome" : "Almeida", 
		"idade" : 18, 
		"sexo" : "Masculino", 
		"profissao" : "NA"
	}
	{ 
		"_id" : ObjectId("582df14e7099709a17b83150"), 
		"nome" : "Osni", 
		"sobrenome" : "Scherer", 
		"idade" : 48, 
		"sexo" : "Masculino", 
		"profissao" : "Businessman", 
		"habilidades" : [
			{
				"nome" : "Visão de Negócio", 
				"nivel" : "Avançado"
			}
		]
	}
	{ 
		"_id" : ObjectId("582df14e7099709a17b83151"), 
		"nome" : "Roseli", 
		"sobrenome" : "Inês", 
		"idade" : 45, 
		"sexo" : "Feminino", 
		"profissao" : "Businesswoman", 
		"habilidades" : [
			{
				"nome" : "Ingles", 
				"nivel" : "Intermediário"
			}
		]
	}
	{ 
		"_id" : ObjectId("582df6e26200e8d8447b707f"), 
		"nome" : "Doravante", 
		"idade" : 1, 
		"sexo" : "Masculino", 
		"profissao" : "NA", 
		"animal" : true, 
		"habilidades" : [
			{
				"nome" : "Bagunçar", 
				"nivel" : "Avançado"
			}
		]
	}
```

Como podemos perceber nem todas as habilidades que possuem um item com o nome __Inglês__ possuem o acento "^" no __Inglês__, foi um
erro de digitação e agora queremos arrumar isso.

### $set
Para isso usaremos o operador do mongodb ```$set```, ele nos possibilita um update na
qual irá alterar apenas o campo de um item de um array sem mexer em outros campos ou itens do array.
Nesse processo vamos utilizar o ```updateMany(<filter>, <update>, <options> [opt])```, então primeiro vamos fazer o filtro, ele ficará
da seguinte forma:

```json
{
	"habilidades.nome" : "Ingles"
}
```
Dessa maneira vamos buscar apenas pelos registros que não possuem o acento no __Inglês__, caso você use esse filtro em um find o banco
lhe retornará:

```
db.Pessoas.find({"habilidades.nome": "Ingles"})
```

```json
{ 
    "_id" : ObjectId("582df06b7099709a17b8314c"), 
    "nome" : "Thaís", 
    "sobrenome" : "Meester", 
    "idade" : NumberInt(16), 
    "sexo" : "Feminino", 
    "profissao" : "NA", 
    "habilidades" : [
        {
            "nome" : "Ingles", 
            "nivel" : "Avançado"
        }
    ]
}
{ 
    "_id" : ObjectId("582df14e7099709a17b8314d"), 
    "nome" : "Jean", 
    "sobrenome" : "Patrick", 
    "idade" : NumberInt(21), 
    "sexo" : "Masculino", 
    "profissao" : "Programador C#", 
    "habilidades" : [
        {
            "nome" : "Ingles", 
            "nivel" : "Avançado"
        }
    ]
}
{ 
    "_id" : ObjectId("582df14e7099709a17b83151"), 
    "nome" : "Roseli", 
    "sobrenome" : "Inês", 
    "idade" : NumberInt(45), 
    "sexo" : "Feminino", 
    "profissao" : "Businesswoman", 
    "habilidades" : [
        {
            "nome" : "Ingles", 
            "nivel" : "Intermediário"
        }
    ]
}
```

Feito o filtro vamos fazer o ```<update>``` utilizando o ```$set```. Quando o banco rodar o ```<filter>``` ele irá trazer os resultados
acima e agora precisamos selecionar o que queremos mudar desses dados, no nosso caso queremos os campos nome dos itens do array 
habilidades que foram filtrados, especificando para o banco ficaria assim:

```json 	
{ 
		"habilidades.0.nome": "Inglês" 
}
```

Em um ```$set```estaríamos dizendo para o banco que queremos mudar o conteúdo do nome no item __0__ do array habilidades de cada 
document do nosso filtro para __Inglês__, então nosso update completo ficaria assim:

```json
db.Pessoas.updateMany(
  { "habilidades.nome" : "Ingles" },
  { $set: 
	  { 
		"habilidades.0.nome": "Inglês" 
	  }
  }
)
```

E o banco nos retorna:

```json
{ 
    "acknowledged" : true, 
    "matchedCount" : NumberInt(3), 
    "modifiedCount" : NumberInt(3)
}
```

Duvida que deu certo? Vamos rodar um find():

```
db.Pessoas.find({})
```

```json
{ 
    "_id" : ObjectId("582deedf7099709a17b8314b"), 
    "nome" : "Johann", 
    "sobrenome" : "Lucas", 
    "idade" : NumberInt(17), 
    "sexo" : "Masculino", 
    "profissao" : "Programador", 
    "habilidades" : [
        {
            "nome" : "Inglês", 
            "nivel" : "Intermediário"
        }
    ]
}
{ 
    "_id" : ObjectId("582df06b7099709a17b8314c"), 
    "nome" : "Thaís", 
    "sobrenome" : "Meester", 
    "idade" : NumberInt(16), 
    "sexo" : "Feminino", 
    "profissao" : "NA", 
    "habilidades" : [
        {
            "nome" : "Inglês", 
            "nivel" : "Avançado"
        }
    ]
}
{ 
    "_id" : ObjectId("582df14e7099709a17b8314d"), 
    "nome" : "Jean", 
    "sobrenome" : "Patrick", 
    "idade" : NumberInt(21), 
    "sexo" : "Masculino", 
    "profissao" : "Programador C#", 
    "habilidades" : [
        {
            "nome" : "Inglês", 
            "nivel" : "Avançado"
        }
    ]
}
{ 
    "_id" : ObjectId("582df14e7099709a17b8314e"), 
    "nome" : "Bruno", 
    "sobrenome" : "Gonçalves", 
    "idade" : NumberInt(32), 
    "sexo" : "Masculino", 
    "profissao" : "Businessman", 
    "habilidades" : [
        {
            "nome" : "Laravel Framework", 
            "nivel" : "Avançado"
        }
    ]
}
{ 
    "_id" : ObjectId("582df14e7099709a17b8314f"), 
    "nome" : "Matheus", 
    "sobrenome" : "Almeida", 
    "idade" : NumberInt(18), 
    "sexo" : "Masculino", 
    "profissao" : "NA"
}
{ 
    "_id" : ObjectId("582df14e7099709a17b83150"), 
    "nome" : "Osni", 
    "sobrenome" : "Scherer", 
    "idade" : NumberInt(48), 
    "sexo" : "Masculino", 
    "profissao" : "Businessman", 
    "habilidades" : [
        {
            "nome" : "Visão de Negócio", 
            "nivel" : "Avançado"
        }
    ]
}
{ 
    "_id" : ObjectId("582df14e7099709a17b83151"), 
    "nome" : "Roseli", 
    "sobrenome" : "Inês", 
    "idade" : NumberInt(45), 
    "sexo" : "Feminino", 
    "profissao" : "Businesswoman", 
    "habilidades" : [
        {
            "nome" : "Inglês", 
            "nivel" : "Intermediário"
        }
    ]
}
{ 
    "_id" : ObjectId("582df6e26200e8d8447b707f"), 
    "nome" : "Doravante", 
    "idade" : NumberInt(1), 
    "sexo" : "Masculino", 
    "profissao" : "NA", 
    "animal" : true, 
    "habilidades" : [
        {
            "nome" : "Bagunçar", 
            "nivel" : "Avançado"
        }
    ]
}

```

Até mais!
