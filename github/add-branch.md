# Adicionando um nova Branch

Para fazer isso deve ser feito os seguintes passo:

1. criar a nova branch e dar um nome a ela. ex.: "ajuste" ``git branch ajuste``
2. fazer o checkout da branch "ajuste" ``git checkout ajuste``
3. enviar a nova branch para o servidor ``git push`` (opcional por enquanto)
4. fazer as alterações necessárias e dar commits no servidor
5. para voltar para a master basta fazer um checkout na master ``git checkout master``
6. quando precisar enviar as alterações da "ajuste" para a "master". na ``master`` deve fazer um merge da ``ajuste``. ``git merge ajuste``