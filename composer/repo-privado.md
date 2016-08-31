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
