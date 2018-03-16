# Monitoração no MongoDB?
Se você quer acompanhar tudo o que está acontecendo no seu banco de dados você pode usar o profiler, lembrando desde já, que ele não deve ser usado sempre porque causa impactos no desempenho.
O Profiler é uma ferramenta fofa, executada no nível do BD, e é utilizada para capturar a informações que estão chegando no Banco de Dados. Ela pode ser usada para detectar problemas de desempenho, debugar a aplicação e até entender como e quando as aplicações estão interagindo com o BD, sem precisar abrir o código fonte da aplicação.
Para habilitar o profiler no MongoDB utilize o comando abaixo:
``` 
db.setProfilingLevel( nível , tempo limite ) 
```

O parâmetro nível especifica um nível do profiler, mais ou menos detalhado, e aceita os valores:
- 0 não coleta informações,
- 1 apenas para operações lentas,
- 2 para todas as operações (seja cuidadoso com esta opção).

O parâmetro tempo limite indica o que o MongoDB deve considerar como uma operação lenta (ou seja, faz todo sentido se você escolheu a opção 1, mas o padrão é 100 ms)
Para saber se o profiler está ativo use a função abaixo  e verifique o atributo was, que terá o mesmo valor do nível escolhido para o profiler.
``` 
db.getProfilingStatus()
``` 

O bacana do profiler é que além de fornecer dados para as ferramentas mongostat e mongotop (que você já vai conhecer), ele permite que você faça várias consultas nas informações coletadas e armazenadas na coleção profile. Te convido a analisar esta coleção, montar as suas consultas e guarda-las com você para quando precisar fazer novamente este tipo de análise. Comece com o mais simples e vá refinando. Para começar execute:
``` 
db.system.profile.find()
```

## Quais as ferramentas disponíveis?  
Vamos conversar é sobre as ferramentas nativas do MongoDB, depois vamos conversar sobre as novidades da versão 3.6.

### mongostat
Quando você baixa o MongoDB uma série de executáveis “vem de brinde” e eu me lembro de dizer que na hora certa saberíamos o uso de quase todos eles.
Um destes executáveis é o mongostat que pode ser executado através da linha de comando ou com um duplo clique no executável.
O [mongostat](https://docs.mongodb.com/manual/reference/program/mongostat/#bin.mongostat) captura e retorna as contagens de operações de banco de dados por tipo (por exemplo, inclusão, consulta, atualização, exclusão, etc.).
Use esta ferramenta fofa para entender a distribuição dos tipos de operação e para fazer ou melhorar o planejamento da capacidade dos seus servidores.

### mongotop
Irmão do mongostat, este também é um dos aplicativos que está disponível junto com o mongo, mongod.
Ele serve para rastrear e relatar as atividades de leitura e gravação em uma instância do MongoDB e relata essas estatísticas por coleção.
Use [mongotop](https://docs.mongodb.com/manual/reference/program/mongotop/#bin.mongotop) para verificar se a atividade e o uso de sua base de dados correspondem às suas expectativas.

## Comandos úteis
Quando o seu aplicativo for disponibilizado para testes ou mesmo em produção é sempre bom conhecer alguns comandinhos para verificar se tudo está de acordo com o esperado.
- [db.currentOp](https://docs.mongodb.com/manual/reference/method/db.currentOp/#db.currentOp) útil para identificar as operações em andamento da instância do banco de dados.
- [db.serverStatus()](https://docs.mongodb.com/manual/reference/method/db.serverStatus/#db.serverStatus), retorna uma visão geral do status do banco de dados, detalhando o uso do disco, uso da memória, conexão, registro no diário e acesso aos índices. O comando retorna o resultado rapidamente e não impacta o desempenho do MongoDB.
- [db.stats()](https://docs.mongodb.com/manual/reference/method/db.stats/#db.stats), retorna um documento com informações sobre armazenamento e volumes de dados. Este comando mostra o espaço de armazenamento utilizado, a quantidade de dados contidos na base de dados, contadores de índice. E informa se o banco de dados está integro (veja o atributo “ok”com o valor 1)… Veja um exemplo da execução deste comando:
``` 
db.stats()
{
“db” : “demo”,
“collections” : 6,
“views” : 0,
“objects” : 17,
“avgObjSize” : 121.82352941176471,
“dataSize” : 2071,
“storageSize” : 122880,
“numExtents” : 0,
“indexes” : 6,
“indexSize” : 122880,
“fsUsedSize” : 105792561152,
“fsTotalSize” : 249695305728,
“ok” : 1
}
```
- [db.collection.stats()](https://docs.mongodb.com/manual/reference/method/db.collection.stats/#db.collection.stats) similar os [dbStats](https://docs.mongodb.com/manual/reference/command/dbStats/#dbcmd.dbStats), mas ao nível da coleção, inclui uma contagem dos objetos na coleção, o tamanho da coleção, a quantidade de espaço em disco usada pela coleção e informações sobre seus índices.
- [rs.status()](https://docs.mongodb.com/manual/reference/method/rs.status/#rs.status)  retorna uma visão geral do status do seu replica set, ele detalha o estado e a configuração do replica set e estatísticas sobre seus membros.
Parecido com o rs.status(), existe também o [sh.status()](https://docs.mongodb.com/manual/reference/method/sh.status/#sh.status), que dá uma visão geral do particionamento e os chuncks.

## E o desempenho?
Nenhum arquiteto ou desenvolvedor está livre das degradações de desempenho que seu banco e dados pode sofrer, sendo assim você não precisa se achar o pior desenvolvedor do mundo se identificar necessidades de ajustes.
É importante fazer tudo certo, desde a primeira vez (nunca caia na história de fazer uma gambiarra hoje para corrigir amanhã. Você não vai corrigir!)
Quando você tem o banco de dados criado, populado e com índices criados, analise o plano de execução das principais queries que você criou! E aqui amigos, não tem fórmula mágica (pelo menos eu ainda não encontrei!), evite COLLSCAN, verifique se os filtros podem ser melhorados, verifique se os índices estão sendo usados, altere os índices e compare os planos de execução.
Os planos de execução além de estatísticas mostram também as escolhas feitas pelo otimizador de consultas.
A função explain com o parâmetro executionStats mostra o plano de execução de uma consulta, através de um documento JSON. As informações que ela retorna incluem:
- Número de documentos retornados pela consulta;
- Número total de documentos lidos;
- Índices utilizados;
- Se a consulta conseguiu retornar resultados sem ter de ler documentos, ou seja se é uma Index Covered Query (mundo perfeito) ;
- Se uma ordenação in-memory foi realizada, o que indica que a criação de um índice pode ser útil;
- O número de entradas do índice que foram escaneadas;
- Quanto tempo a consulta levou para retornar, em ms;
- Quais outros planos de execução foram rejeitados pelo motor de consulta do Mongo, indicando ainda o tempo que essa decisão levou, geralmente 0ms (o que indica menos que 1ms)

Sintaxe para verificar o plano de execução de uma consulta:
``` 
db.nome da coleçao.find ( { atributo : valor procurado } ).explain("executionStats")
```

E se você quiser ver o plano de execução em um formato visual… Use o Mongo Compass, que é uma ferramenta fofa, tem uma versão gratuita, e apresenta o plano de execução de uma query de forma visual.

##E as novidades?
Com a versão 3.6 do MongoDB tivermos muitas melhorias no desempenho em geral. Mas temos também novidades na monitoração do banco de dados.

## MongoDB Ops Manager
O Ops Manager é um pacote para gerenciar implantações do MongoDB. O Ops Manager fornece o Ops Manager Monitoring e o Ops Manager Backup, que ajuda os usuários a otimizar clusters e mitigar riscos operacionais. Olha que lindo!
Essa ferramenta fantástica fornece relatórios, visualizações e alertas em tempo real em indicadores de banco de dados e hardware.
Como funciona: um agente de monitoração leve funciona dentro de sua infraestrutura e coleta estatísticas dos nós cluster do MongoDB. O agente transmite as estatísticas do banco de dados de volta ao Ops Manager para fornecer relatórios em tempo real. Você pode configurar alertas sobre indicadores que você escolher. Ou seja, se você quer monitorar o desempenho, você consegue, quer monitorar backup, IO, consegue também, tudo de acordo com a sua necessidade!

## MongoDB Cloud Manager
Mas e se você optou por criar seu banco de dados na nuvem utilizando o MongoDB Atlas? A versão 3.6 trás novidades para você também!
Projetado pela equipe que desenvolve o MongoDB, o Cloud Manager fornece um pacote completo para gerenciar implantações do MongoDB.
O MongoDB Cloud Manager é um serviço para gerenciar, monitorar e fazer backup de uma infraestrutura MongoDB. Além disso, o Cloud Manager permite que os administradores mantenham um pool de servidores para facilitar a implantação do MongoDB.
Com muitas semelhanças MongoDB Ops Manager, é possível ter um controle fino sobre os seus bancos de dados na nuvem, e assim atuar na melhoria do desempenho sempre que for preciso.

## Conclusão
Um aplicativo de sucesso não está finalizado quando você termina de codificá-lo!
Verifique as suas queries, valide os índices que você criou veja o que pode ser melhorado. E isso independe do SGBD que você está utilizando.
No caso do MongoDB há varias ferramentas que vão te ajudar na missão de validar suas queries e de cuidar do seu ambiente!
Use as ferramentas, faça testes, mude o que precisa ser mudado!
E tenha certeza, você estará mais perto do sucesso!
