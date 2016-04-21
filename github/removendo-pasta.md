# Removendo uma pasta inteira de um repositório GitHub

Algumas vezes é enviado a pasta `.idea` (pasta oculta) de controle do PhpStorm para o projeto e agora é preciso remove-la. Mas o próprio PhpStrom não exibe esta pasta.

Então é preciso executar o comando abaixo para marcar a pasta `.idea` como removida do projeto.

    git rm -r .idea

Pronto, agora a pasta roi removida, basta fazer um commit e push para que a alteração vá para o github.
