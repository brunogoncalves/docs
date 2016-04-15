# SSL

Para instalar um certificado SSL no apache:

Após a solicitação do certificado for aprovada, será possível baixar o SSL e o certficado intermediário, onde os mesmos, precisam ser intalados no seu servidor da Web.

Onde também, é possível baixar o certificado intermediário no `repositório`.

## Para instalar SLL e certificados intermediários:

Copie o arquivo do certificado SSL e do pacote de certificado para seu servidor Apache. Você já deve ter um arquivo de chave no servidor de quando a solicitação de certificado foi gerada.

Encontre as diretivas a seguir no seu arquivo `httpd.conf` ou `ssl.conf` (os arquivos que você utiliza dependem de como o Apache foi configurado). Se uma ou mais delas já tiver comentários, remova-os excluindo o caractere `#` do início da linha. Defina os valores dessas diretivas para o caminho absoluto e nome do arquivo adequado, com base na sua versão do Apache:

Apache versão < 2.4.8

                 Diretiva   | Caminho a ser inserido

          SSLCertificatFile | Caminho do arquivo de certificado

      SSLCertificateKeyFile |  Caminho do arquivo de chave

    SSLCertificateChainFile | Caminho do pacote intermediário

Apache versão 2.4.8+

                 Diretiva   | Caminho a ser inserido

          SSLCertificatFile | Caminho do arquivo de certificado

      SSLCertificateKeyFile |  Caminho do arquivo de chave

       SSLCACertificatePath | Caminho do pacote intermediário

Salve seu arquivo de configuração e reinicie o Apache.

## Para reiniciar seu servidor da Web:

O procedimento para reiniciar o Apache varia muito de acordo com a plataforma de sistema operacional. Normalmente, em plataformas tipo Unix (Linux, Solaris, HP-UX, etc.), é necessário executar um script e reiniciar o daemon httpd. No Windows, geralmente você para e reinicia o serviço Apache no console administrativo de serviços. Consulte o fornecedor do seu sistema operacional ou a documentação do Apache.

