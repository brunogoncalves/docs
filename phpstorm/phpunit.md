# Configurando o PhpUnit no PhpStorm


Inclua o phpunit no seu composer.json, ex:

    "require-dev": {
        "phpunit/phpunit": "~4.1"
       }

Execute o comando update do composer na matriz do projeto pelo console:

    composer update

Crie o arquivo phpunit.xml na matriz do projeto e configure-o, ex:

    <?xml version="1.0" encoding="UTF-8"?>
     <phpunit backupGlobals="false"
         backupStaticAttributes="false"
         bootstrap="tests/bootstrap.php"
         colors="true"
         convertErrorsToExceptions="true"
         convertNoticesToExceptions="true"
         convertWarningsToExceptions="true"
         processIsolation="false"
         stopOnError="false"
         stopOnFailure="false"
         syntaxCheck="true"
         verbose="true"
    >
    <testsuites>
        <testsuite name="NetForce Framework Test Suite">
            <directory suffix="Test.php">./tests/</directory>
        </testsuite>
    </testsuites>
    <php>
        <env name="APP_ENV" value="testing"/>
        <env name="CACHE_DRIVER" value="array"/>
        <env name="SESSION_DRIVER" value="array"/>
        <env name="QUEUE_DRIVER" value="sync"/>
    </php>
   </phpunit>
   
   Entre nas configurações do seu PhpStorm:
   
   ![Settings](https://raw.githubusercontent.com/brunogoncalves/docs/master/phpstorm/imgs/print-settings.jpg)
   

   Em seguida enter nas configurações do PhpUnit dentro do item PHP:
   
   ![Phpunit](https://raw.githubusercontent.com/brunogoncalves/docs/master/phpstorm/imgs/print-phpunit.jpg)
   
   
   Selecione "Use custom loader" e em seguida em "Path to script" passe o caminho do phpunit:
   
   ![Phpunit2](https://raw.githubusercontent.com/brunogoncalves/docs/master/phpstorm/imgs/print-library.jpg)
   
   
   Por final em "Test Runner" selecione "Default configuration file" e passe o caminho do phpunit.xml criado anteriormente:
   
   ![Phpunit3](https://raw.githubusercontent.com/brunogoncalves/docs/master/phpstorm/imgs/print-testrunner.jpg)
