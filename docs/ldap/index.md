# LDAP

## Instalação

Para poder usar o LDAP, é preciso instalar o servidor samba, e para isso usamos o seguinte comando

É preciso de uma máquina virtual linux com o samba e uma maquina com windowns 7 para se comunicar com o samba;

Para instalar o samba na maquina virtual linux você precisará dar os seguintes comandos:

    apk add samba-dc krb5


## Configuração

Para configurar precisaremos colocar um nome para nossa máquina virtual

- No caso o nome ficou noronha.pernambuco.lab

E o nome do dominio

- No caso será pernambuco.lab

Para colocar o domínio na máquina virtual windows você fará o seguinte:

1 - Primeiro entre na mv linux e em /etc/network/interfaces

Lá você define o ip estatico para a interface desejada.

2 - Depois acesse propriedades de protocolo TCP/IP Ipv4 e configure a rede

Desta maneira:

[![configIP](https://i.im.ge/2023/12/29/xxLi9P.configIP.png)](https://im.ge/i/xxLi9P)

Depois disso vá em "Painel de controle" > "Sistema e Segurança" > "Sistema" > "Alterar configurações"

Você abrirá uma aba de propriedades do sistema, nela você pode alterar o nome da máquina e definir um domínio para acessar.

Após definir o domínio "pernambuco.lab" você conseguirá acessar o servidor samba que está na máquina linux da sua maquina virtual linux.

#### Agora vamos criar as OUs

Para criar uma nova OU (Unidade Organizacional) vamos na maquina windows, procure no barra de pesquina por "Usuários e Computadores do Active Diretory"

Ao acessar você vera algumas OUs padrão do domínio pernambuco.lab.

Clique numa pasta de nome "Unidade Organizacional", ou clique com o botão direito do mouse que você verá a opção.

Crie duas OUs, uma de nome "vendedores" e outra de nome "rh"

#### Criando os grupos

*Dentro da OU `vendedores` vamos criar o grupo `oliveira`
*Dentro da OU `rh` vamos criar o grupo `silvestre`

Para criar os grupos basta clicar com o botão direito do mouse, depois em "novo" e "grupo"

#### Criando os usuários

Para cada pasta vamos criar 4 usuários, para criar os usuários clicamos com o botão direito do mouse, "Novo" > "Usuário"

[![grupoexemplo](https://i.im.ge/2023/12/29/xxUeCS.grupoexemplo.png)](https://im.ge/i/xxUeCS)

Após criar todos os usuários, mover eles para dentro das OUs desejadas.

Ficarão dessa forma:

[![OUvendedores](https://i.im.ge/2023/12/29/xxhrl9.OUvendedores.png)](https://im.ge/i/xxhrl9)
[![OUrh](https://i.im.ge/2023/12/29/xxhu0X.OUrh.png)](https://im.ge/i/xxhu0X)

Depois basta adicionar os usuários de cada pasta dentro de seu grupo.

Para fazer isso, basta selecionar todos os usuários, clicar com o botão direito do mouse e "Adicionar a um grupo"

Lá basta digitar o nome do grupo que você deseja.

Eles ficarão assim:

[![GrupoOliveira](https://i.im.ge/2023/12/29/xxhCMa.GrupoOliveira.png)](https://im.ge/i/xxhCMa)
[![GrupoSilvestre](https://i.im.ge/2023/12/29/xxhxEy.GrupoSilvestre.png)](https://im.ge/i/xxhxEy)

#### Criando pastas compartilha

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

