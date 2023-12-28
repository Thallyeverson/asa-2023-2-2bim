# SMB

## Instalação

É preciso de uma máquina virtual linux com o samba e uma maquina com windowns 7 para se comunicar com o samba;

Para instalar o samba na maquina virtual linux você precisará dar os seguintes comandos:

    apk add samba-dc krb5


## Configuração

#### Criando os grupos

*Dentro da OU `vendedores` vamos criar o grupo `oliveira`
*Dentro da OU `rh` vamos criar o grupo `silvestre`

Para criar os grupos basta clicar com o botão direito do mouse, depois em "novo" e "grupo"

#### Criando os usuários

Para cada pasta vamos criar 4 usuários, para criar os usuários clicamos com o botão direito do mouse, "Novo" > "Usuário"

[![grupoexemplo](https://i.im.ge/2023/12/29/xxUeCS.grupoexemplo.png)](https://im.ge/i/xxUeCS)

Após criar todos os usuários.

Ficarão dessa forma:

[![OUvendedores](https://i.im.ge/2023/12/29/xxhrl9.OUvendedores.png)](https://im.ge/i/xxhrl9)
[![OUrh](https://i.im.ge/2023/12/29/xxhu0X.OUrh.png)](https://im.ge/i/xxhu0X)

Depois basta adicionar os usuários de cada pasta dentro de seu grupo.

Para fazer isso, basta selecionar todos os usuários, clicar com o botão direito do mouse e "Adicionar a um grupo"

Lá basta digitar o nome do grupo que você deseja.

Eles ficarão assim:

[![GrupoOliveira](https://i.im.ge/2023/12/29/xxhCMa.GrupoOliveira.png)](https://im.ge/i/xxhCMa)
[![GrupoSilvestre](https://i.im.ge/2023/12/29/xxhxEy.GrupoSilvestre.png)](https://im.ge/i/xxhxEy)


#### Criando pastas compartilhada

Para criar as pastas compartilhadas para esses grupos vamo na mv linux e usamos o código:
    mkdir /srv/samba/oliveira
    mkdir /srv/samba/silvestre

serão criadas pastas no serviço samba e elas serão configuradas da seguinte forma:

acessando o aquivo "/etc/samba/smb.conf"

[![CONFIGDECOMPARTILHAMENTO](https://i.im.ge/2023/12/29/xxiAFC.CONFIGDECOMPARTILHAMENTO.png)](https://im.ge/i/xxiAFC)

após isso é só entrar na máquina windows, digitar o comando "\\noronha" que é o nome da máquina e ver as pastas compartilhadas. 
Elas só poderão ser acessadas pelos usuários especificos de cada grupo.

[![usuárioOliveira](https://i.im.ge/2023/12/29/xx0Uam.usuarioOliveira.png)](https://im.ge/i/xx0Uam)
[![usuariosilvestre](https://i.im.ge/2023/12/29/xx0x1z.usuariosilvestre.png)](https://im.ge/i/xx0x1z)

-   Se tentar acessar a pasta com um usuário de um outro grupo, aparecerá essa mensagem:

[![usuarioerrado1](https://i.im.ge/2023/12/29/xx9onh.usuarioerrado1.png)](https://im.ge/i/xx9onh)
[![usuarioerrado2](https://i.im.ge/2023/12/29/xx9LkW.usuarioerrado2.png)](https://im.ge/i/xx9LkW)


Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

1. Criar 2 grupos para dois de seus sobrenomes;
2. Criar 4 usuários, dois para cada um dos sobrenomes;
3. Compartilhar duas pastas com dois de seus sobrenome, compartilhado para o grupo com o sobrenome correspondente.




