# PROXY

Um proxy atua como intermediário entre um dispositivo e a internet. Ele recebe solicitações do dispositivo, encaminha essas solicitações para os servidores da internet e, em seguida, retorna as respostas aos dispositivos. Isso permite ocultar o endereço IP do dispositivo, melhorar a segurança, e filtrar ou modificar o tráfego para diversos fins, como controle de acesso ou otimização de desempenho.

## Instalação

Para configurar os proxy na maquina temos primeiro que instalar o pacote squid, e para fazer essa instalação usados o comando:

    sudo apt update
    sudo apt install squid

## Configuração

Para configurar, por medidas de segurança fazemos uma cópia do arquivo de configuração do squid.

Usamos o seguinte comando:

    sudo cp /etc/squid/squid.conf /etc/squid/squid.conf.bak

Feito a cópia, agora podemos fazer as configurações.

usando o comando
    nano /etc/squid/squid.conf
entramos no arquivo de configuração podemos adicioar as linhas de comando proxy

## ACLs

As Listas de Controle de Acesso (ACLs) em um proxy referem-se a regras que controlam ou filtram o tráfego com base em critérios específicos, como endereços IP, portas ou tipos de conteúdo. Essas ACLs ajudam a gerenciar o acesso e definir políticas de segurança no proxy, determinando quais solicitações são permitidas ou bloqueadas.

Configuramos no browser, o ip e a porta para habilitar o proxy na máquina:

[![configuraçãositeproxy](https://i.im.ge/2024/01/03/3MxhJK.configuracaositeproxy.png)](https://im.ge/i/3MxhJK)

As ACLs usadas como regras para os testes foram as seguintes:
```
acl site_ban dstdomain .facebook.com .wikipedia.org .globo.com
acl firefox browser Firefox
acl hora_entrada time MTWHF 21:30-23:59
acl ipblock dst 104.16.36.133
```

E para aplicar essas regras usamos os comandos:

```
http_access deny site_ban
http_access allow hora_entrada
http_access deny firefox
http_access deny ipblock
```
    

Basicamente, 

ACL 1: bloqueia os dominios do facebook, wikipedia e globo;

ACL 2: bloqueia o browser firefox;

ACL 3: habilita o usuário para usar a maquina no horário definido;

ACL 4: bloquia o acesso ao ip do instagram;


Incluir o(s) nome(s) e o conteúdo do(s) arquivo(s) de configuração.

Fazer a configuração de 4 ACLs distintas, conforme a atividade passada em sala de aula.

## Teste


O arquivo de configuração ficou assim:

[![acls_permissoes](https://i.im.ge/2024/01/03/3MEbe6.acls-permissoes.png)](https://im.ge/i/3MEbe6)

Os logs de utilzaçõa das regras:

[![Tempo_real](https://i.im.ge/2024/01/03/3ME4vp.Tempo-real.png)](https://im.ge/i/3ME4vp)

Os sites que as regras proxys foram definidas, ficaram da seguinte maneira:

[![globo_block](https://i.im.ge/2024/01/03/3MxAnq.globo-block.png)](https://im.ge/i/3MxAnq)
[![wikipedia_block](https://i.im.ge/2024/01/03/3MxxPP.wikipedia-block.png)](https://im.ge/i/3MxxPP)
[![facebook](https://i.im.ge/2024/01/03/3Mxbuf.facebook.png)](https://im.ge/i/3Mxbuf)

Ao tentar usar o github com a permissão de browser, não é permitido

[![GITHUB](https://i.im.ge/2024/01/03/3M3S4C.GITHUB.png)](https://im.ge/i/3M3S4C)

E após entrar no tempo definido na regra da 3ª linha, o site github é habilitado para uso

[![githubtempo](https://i.im.ge/2024/01/03/3M3fbD.githubtempo.png)](https://im.ge/i/3M3fbD)