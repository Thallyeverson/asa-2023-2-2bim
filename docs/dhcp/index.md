# DHCP

O DHCP (Dynamic Host Configuration Protocol) é um protocolo de rede que automatiza a atribuição de endereços IP e configurações relacionadas a dispositivos em uma rede. Em vez de configurar manualmente cada dispositivo com um endereço IP, gateway e servidor DNS, o DHCP permite que os dispositivos obtenham essas informações automaticamente do servidor DHCP da rede. Isso simplifica a administração de redes, pois os endereços IP são atribuídos dinamicamente, facilitando a adição ou remoção de dispositivos na rede sem a necessidade de intervenção manual.

## Instalação

Para esse processo precisamos de uma maquina virtual linux e uma maquina windows xp, a linux servirá para nosso servidor DHCP e a windows xp será nosso cliente.

Para instalarmos o DHCP, precisamos instalar o pacote dnsmask, que oferece um servidor DHCP, alem de disponibilizar também servidores dns e TFTP

O comando para instalar é:

    apk add dnsmasq


## Configuração

Primeiro definimos a ip do servidor DHCP nas configurações de redes,

[![dnsrede](https://i.im.ge/2024/01/04/3XvQE6.dnsrede.png)](https://im.ge/i/3XvQE6)

Apos isso, vamos configurar o arquivo do DHCP. Eu nomeei como /etc/dnsmasq.d/asa.conf e quando acessar precisamos definir o range dos IPs

para acessar usei o editor de texto nano, portanto ficou assim o comando:

    nano /etc/dnsmasq.d/asa.conf

[![configDHCP](https://i.im.ge/2024/01/04/3XvXSK.configDHCP.png)](https://im.ge/i/3XvXSK)

Após feita a configuração na maquina linux, vamos para a windows configurar os clientes.

Vamos fazer configurações para duas máquinas, uma ficará com o ip reservado pelo endereço mac dela e outra pegará um ip aleatório dentro do range definido.

Vamos em "configuração de rede", protocolo "TCP/IP" e lá definimos para pegar os IP automaticamente no servidor DHCP, e também colocamos o DNS prefercial e o alternativo. 

Ficará dessa forma:

[![DHCPclientconfig](https://i.im.ge/2024/01/04/3X4MIr.DHCPclientconfig.png)](https://im.ge/i/3X4MIr)

Quando terminado a configuração, restartamos o dnsmasq e reiniciamos as maquinas 

Para restartar o servidor DHCP usamos o seguinte comando:

    rc-service dnsmasq restart




## Teste

A configuração da maquina que pegará um IP aleatório dentro do Range ficará assim:

[![cloneDHCP](https://i.im.ge/2024/01/04/3X4SMJ.cloneDHCP.png)](https://im.ge/i/3X4SMJ)

E a máquina onde foi definido um ip fixo para ela ficará assim:

[![fixoconfig](https://i.im.ge/2024/01/04/3XBoUh.fixoconfig.png)](https://im.ge/i/3XBoUh)

