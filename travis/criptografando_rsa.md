# Criptografando um arquivo RSA para o Travis

Quando for preciso utilizar uma chave privada rsa no travis, você deve criptografa-la para que a sua chave não fique publica no repositório.
Para isso é preciso seguir os passos abaixo para garantir que a chave ssh utilizada no projeto não esteja exposta.

**OBS: Esse procedimento deve ser feito em uma máquina linux ou mac, no windows gera problemas na hora de criptografar**
**Também deve ser feito na pasta que foi clonado o projeto do github**

1. Vamos gerar o par de chaves

    ```
    ssh-keygen -t rsa -b 4096 -C "seu@email.com" -f ./travis_git_rsa
    ```
    Quando for solicitado a senha, **deixa-a em branco**.
    O comando acima irá gerar um par de chaves e agora você deve ter os arquivos `travis_git_rsa` e o `travis_git_rsa.pub`

2. Agora, vamos criptografar a chave privada o arquivo `travis_git_rsa`:
    Lembre-se que esse procedimento deve ser feito na pasta do projeto onde foi clonado do github e onde encontramos o arquivo `.travis.yml`

    ```
    $travis encrypt-file travis_git_rsa --add

    encrypting travis_git_rsa for <repo...>
    storing result as travis_git_rsa.enc
    storing secure env variables for decryption

    Make sure to add travis_git_rsa.enc to the git repository.
    Make sure not to add travis_git_rsa to the git repository.
    Commit all changes to your .travis.yml.
    ```
    Neste momento já foi gerado o arquivo `travis_git_rsa.enc`, que é nossa chave privada criptogravada para ser utilizada pelo travis. Também foi inserido no projeto do travis as variáveis de ambiente `encrypted_<...>_iv` e a `encrypted_<...>_key` que são as chaves que só o travis sabe para descriptografar nosso arquivo.

    **OBS: É EXTREMAMENTE importante, que você adicione os arquivos da chave `travis_git_rsa` e o `travis_git_rsa.pub` no `.gitignore` para evitar que esses dois arquivos sejam enviados para nosso repositório público e assim expor nossa chave. Somente o arquivo criptografado `travis_git_rsa.enc` deve ser adicionado no projeto.**

3. Nesse passo verificamos também que nosso arquivo `.travis.yml` foi modificado e nele foi adicionado algumas linhas parecidas com o exemplo abaixo:

    ```
    before_install:
      - openssl aes-256-cbc -K $encrypted_<..>_key -iv $encrypted_<..>_iv 
       -in travis_git_rsa.enc -out travis_git_rsa -d 
    ```

4. Agora você precisa registrar a nova chave no GitHub, para isso você deve copiar o conteúdo no arquivo `travis_git_rsa.pub` e adicionar nas lista de chaves `SSH` do seu usuário do github. Em Settings.

5. Feito isso basta efetuar o `commit` e o `push` que o trevis irá fazer o resto.