# MongoDB - Instalação

# Linux

## Preparando repositório

Para usar o instalado yum, deve antes ser habilitado o repositorio
```
    vim /etc/yum.repos.d/mongodb.repo
```

E preencher com o conteúdo abaixo

```
    [mongodb]
    name=MongoDB Repository
    baseurl=http://downloads-distro.mongodb.org/repo/redhat/os/x86_64/
    gpgcheck=0
    enabled=1
```

Agora para instalar execute o comando abaixo:
```
    yum install mongo-10gen mongo-10gen-server
```

Feito isso agora você terá um serviço mongod como serviço linux

Referência: 
 - Linux 6 [https://www.liquidweb.com/kb/how-to-install-mongodb-on-centos-6/](https://www.liquidweb.com/kb/how-to-install-mongodb-on-centos-6/)
 - Linux 7 [https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-centos-7](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-centos-7)

# Windows

## Download

Para fazer a instalação do MongoDB no windows, primeiro baixe-o no seguite site: "https://www.mongodb.com/download-center#community",
depois de ter feito o download execute o arquivo .msi e faça todos os procedimentos pedidos.

## Instalação
- A primeira coisa recomendada a ser feita é por o bin do MongoDB no path do windows, então faça isso.
O caminho provável do bin é "C:\Program Files\MongoDB\Server\<versãoMongoDB>\bin"


### MongoDB Service
> O **mongod.exe** é o server do MongoDB


Para não ter que iniciar o ```mongod``` toda vez que for o usar o MongoDB, iremos criar um serviço para o MongoDB, dessa maneira
siga os passos a seguir:

1. Abra o cmd como administrador

  Aperte a ```Win``` key e digite cmd, depois aperte ```CTRL + SHIFT + ENTER``` para abrir o cmd como administrador.


2. Crie diretórios

  O MongoDB necessita de diretórios para armazenar o db e os logs, crie eles preferencialmente seguindo o padrão a seguir:

  ``` mkdir c:\data\db ```
  ``` mkdir c:\data\log ```


3. Crie um configuration file

  Não é necessariamente preciso a criação de um arquivo de configuração, mas é o mais recomendado. Claro que você pode fazer a instalação do
  serviço do mongod apenas com um comando no cmd passando como parâmetro os diretórios do db e do log.

  O arquivo de configuração será um arquivo ```.cfg``` e terá que especificar o ```systemLog.path``` e o ```storage.dbPath```, portanto crie
  o arquivo seguindo o modelo abaixo:

```
systemLog: 
    destination: file 
    path: c:\data\log\mongod.log
storage:
    dbPath: c:\data\db 
```
> Tome cuidado com o configuration file, ele costuma dar problemas por causa do tab, caso dê problema tente identar o texto apertando
4 vezes a tecla espaço em cada campo necessário, assim como segue o modelo acima.

Preferencialmente coloque o serviço no diretório bin do MongoDB com o nome ```mongod.cfg```


4. Criar o MongoDB Service

Finalmete para criar o serviço do MongoDB execute o seguinte comando no cmd:

```
mongod --config "C:\Program Files\MongoDB\Server\3.6\bin\mongod.cfg" --install
```
ou 
```
sc.exe create MongoDB binPath= "\"C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe\" --service --config=\"C:\Program Files\MongoDB\Server\3.2\mongod.cfg\"" DisplayName= "MongoDB" start= "auto"
```

Caso você tenha usado o segundo jeito e tenha sucesso na operação, retornará a seguinte mensagem:

``` [SC] CreateService SUCCESS ```

Por fim, inicialize o MongoDB Service com o seguinte comando:

``` net start MongoDB ```

Se você tiver como retorno...

| Inglês | Português |
| ------ | --------- |
| System Error 2 has occurred. | Erro de sistema 2. |
| The system cannot find the file specified. | O sistema não pode encontrar o arquivo especificado. |

...remova o serviço e tente novamente...

```
mongod --remove
mongod --config "C:\Program Files\MongoDB\Server\3.6\bin\mongod.cfg" --install 
net start MongoDB
```

Feito todos esses passos o seu MongoDB já estará rodando perfeitamente, bem vindo ao mundo NoSQL.


