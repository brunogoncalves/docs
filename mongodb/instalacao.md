# MongoDB - Instalação

## Windows

### Download

Para fazer a instalação do MongoDB no windows, primeiro baixe-o no seguite site: "https://www.mongodb.com/download-center#community",
depois de ter feito o download execute o arquivo .msi e faça todos os procedimentos pedidos.

### Instalação

- A primeira coisa recomendada a ser feita é por o bin do MongoDB no path do windows, então faça isso.
O caminho provável do bin é "C:\Program Files\MongoDB\Server\<versãoMongoDB>\bin"

#### MongoDB Service
- O mongod.exe é o server do MongoDB

Para não ter que iniciar o ```mongod``` toda vez que for o usar o MongoDB, iremos criar um serviço para o MongoDB, dessa maneira
siga os passos a seguir:

1. Abra o cmd como administrador

Aperte a ```Win``` key e digite cmd, depois aperte ```CTRL + SHIFT + ENTER``` para abrir o cmd como administrador.

2. Crie diretórios

O MongoDB necessita de diretórios para armazenar o db e os logs, crie eles preferencialmente seguindo o padrão a seguir:

``` mkdir c:\data\db
    mkdir c:\data\log```

3. Crie um configuration file

Não é necessariamente preciso a criação de um arquivo de configuração, mas é o mais recomendado. Claro que você pode fazer a instalação do
serviço do mongod apenas com um comando no cmd passando como parâmetro os diretórios do db e do log.

O arquivo de configuração será um arquivo ```.cfg``` e terá que especificar o ```systemLog.path``` e o ```storage.dbPath```, portanto crie
o arquivo seguindo o modelo abaixo:

``` systemLog:
    destination: file
    path: c:\data\log\mongod.log
    storage:
    dbPath: c:\data\db ```

Preferencialmente coloque o serviço no diretório bin do MongoDB com o nome ```mongod.cfg```

4. Criar o MongoDB Service

Finalmete para criar o serviço do MongoDB execute o seguinte comando no cmd:

```sc.exe create MongoDB binPath= "\"C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe\" --service --config=\"C:\Program Files\MongoDB\Server\3.2\mongod.cfg\"" DisplayName= "MongoDB" start= "auto"```

Caso você tenha sucesso na operação retornará a seguinte mensagem:

``` [SC] CreateService SUCCESS ```

Por fim, inicialize o MongoDB Service com o seguinte comando:

```net start MongoDB```

Feito todos esses passos o seu MongoDB já estará rodando perfeitamente, bem vindo ao futuro.