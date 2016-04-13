# Usuários

- [Configurar o Shell/False](#configurar-shell-false)
- [Criar usuário](#criar-usuario)
- [Adicionar o usuário ao grupo root](#adicionar-usuario-root)
- [Senha para o usuário](#senha-usuario)
- [Definir propriedade sobre a pasta home](#propriedade-home)


Para criar usuários que não irão fazer login no sistema (ssh) mas será utilizado no APACHE e FTP

Devemos associá-los ao shell/false

<a name="configurar-shell-false"></a> 
## Para configurar o shell/false:

    vim /etc/shells

Adicione o /bin/false na lista se não tiver

<a name="criar-usuario"></a> 
## Para criar um usuário:

    useradd usuario -d /dados/www/ -s /bin/false -N

<a name="adicionar-usuario-root"></a> 
## Adicionando o usuário criado ao grupo root:

    gpasswd -a usuario root

<a name="senha-usuario"></a> 
## Definindo uma senha para o usuário:

    passwd usuario

<a name="propriedade-home"></a> 
## Definir propriedade sobre a pasta "home":

    chown usuario:root /dados/www




