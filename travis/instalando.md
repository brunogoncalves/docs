# Instalando Travis no Ubuntu

Para instalar o TravisCI CLient no Ubuntu você deve seguir os passos abaixo:

1. Primeiro você deve instalar o ruby par adepois instalar o travis

    ```bash
        sudo apt install ruby ruby-dev
    ```

2. Depois basta executar o comando abaixo para instalar o travis

    ```bash
        sudo snap install travis
    ```

3. Para testar que o travis foi instalado com sucesso, execute o comando abaixo e seré exibido a versão instalada no travis:

    ```bash
        travis -v
    ```