# Usando repositórios privados

## Repositório Local

```json
"repositories": [
        {
            "type": "vcs",
            "url" : "C:\framework"
        }
    ]
```

## Repositório Privado no GitHub

```json
    "repositories": [
        {
            "type": "git",
            "url" : "https://github.com/brunogoncalves/docs.git"
        }
    ]
```

## Se precisar configurar o token no composer

    composer config -g github-oauth.github.com <oauthtoken>

## Configurar o SSH no Windows

Quando você for ter a dependência de um repositório privado em seu projeto, você precisa ter uma
SSH key válida para poder utilizar o mesmo. Siga os seguintes passos para configurar uma SSH Key na sua máquina.

### Configurando uma SSH Key na sua máquina

- Caso você não tenha gerado e/ou adicionado uma SSH Key no GitHub, entre nesse link https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/ para gerar a key e/ou entre nesse link para adicionar a sua ssh key no GitHub https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/.

- Para poder utilizar sua SSH Key você precisa colocar o caminho da sua pasta `mingw32/bin` onde contém o `git.exe` e o caminho da sua pasta `usr/bin` onde contém o `ssh.exe` no path do Windows.

- O caminho provável para estas pastas é o **C:\Users\YourUser\AppData\Local\GitHub\PortableGit_numbers-and-letters**, nesse diretório você encontrará as duas pastas citadas acima, então apenas coloque-as no path do Windows (Sistema -> Configurações Avançadas do Sistema -> Variáveis de Ambiente...)
