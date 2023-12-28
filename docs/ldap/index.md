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



Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

- Criar duas OU: `vendedores` e `rh`;
- Mover o grupo `sobrenome1` e seus membros para a OU `vendedores`;
- Mover os grupo `sobrenome2` e seus membros para a OU `rh`.

## Teste


