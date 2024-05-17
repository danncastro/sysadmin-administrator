---
description: >-
  A camada de transporte possibilita que diversas aplicações troquem dados
  simultaneamente (multiplexação).
---

# Introdução: Camada de Transporte

Cada aplicação utiliza uma porta diferente, TCP ou UDP.

Do lado cliente, temos portas que acessam o servidor "daemon" através de portas específicas.

As redes de dados e a Internet suportam a rede humana através do fornecimento de comunicação contínua e confiável entre pessoas a múltiplos serviços como e-mail, web, mensagens instantâneas, etc...

Dados de cada uma dessas aplicações são empacotadas, transportadas e entregues ao servidor daemon apropriado ou aplicação no dispositivo de destino.

Os processos descritos na camada de Transporte do modelo OSI aceitam dados da Camada de Aplicação e os preparam para endereçamento na camada de Rede.

A Camada de Transporte é responsável pela transferência fim-a-fim de dados da aplicação.

## <mark style="color:red;">Propósito da camada de transporte</mark>

A camada de Transporte proporciona a segmentação de dados e o controle necessário para reagrupar esses segmentos em fluxos de comunicação. Suas responsabilidades primárias para realizar isto são:

* Identificar as diferentes aplicações nos hosts de origem e destino.&#x20;
* Segmentar dados e gerenciar cada segmento.
* Reagrupar os segmentos em fluxos de dados de aplicação.

### <mark style="color:red;">Identificação das Aplicações:</mark>

Qualquer host pode ter múltiplas aplicações que se comunicam através da rede. Cada uma destas aplicações irá se comunicar com uma ou mais aplicações em hosts remotos. É responsabilidade da camada de Transporte manter fluxos múltiplos de comunicação entre estas aplicações

Para passar os fluxos de dados para as aplicações apropriadas, a camada de Transporte deve identificar a aplicação de destino. Para realizar isso, a camada de Transporte designa à aplicação um identificador (número de porta)

A camada de Transporte é o link entre a camada de Aplicação e a camada de rede. Esta camada aceita dados de diferentes conversações e os passa para as camadas inferiores como segmentos gerenciáveis que podem ser finalmente multiplexados no meio

As aplicações não precisam saber dos detalhes operacionais da rede em uso. As aplicações geram dados que são enviados de uma aplicação a outra, sem considerar o tipo de host de destino, o tipo de meio sobre o qual o dado deve trafegar, o caminho tomado pelo dado, o congestionamento em um link, ou o tamanho da rede. Da mesma forma, as camadas inferiores não possuem conhecimento sobre a existência de múltiplas aplicações

***

### <mark style="color:red;">Segmentação de Dados:</mark>

Como cada aplicação cria um fluxo de dados para ser enviado a uma aplicação remota, estes dados devem ser preparados para serem enviados através do meio em segmentos gerenciáveis. Os protocolos de camada de Transporte descrevem serviços que segmentam estes dados a partir da camada de Aplicação. Isto inclui o encapsulamento necessário em cada lado do segmento. Cada segmento de dados de aplicação requer a adição de cabeçalhos da camada de Transporte para indicar a qual comunicação (circuito virtual) ele está associado.

***

### <mark style="color:red;">Reagrupamento de Segmentos</mark>

No host de destino, cada segmento de dados pode ser direcionado para a aplicação apropriada. Em adição a isso, estes segmentos de dados individuais também precisam ser reconstruídos em um fluxo completo de dados que seja útil para a camada de Aplicação. Os protocolos da camada de Transporte descrevem como a informação do cabeçalho da camada de Transporte é usada para reagrupar os segmentos de dados em fluxos a serem passados para a camada de Aplicação.

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Necessidades de cada aplicação</mark>

> “Protocolos diferentes precisam de métodos de entrega diferentes!”

Determinadas aplicações precisam de confiabilidade na entrega dos dados ao destino, onde pequenos atrasos são aceitáveis para realizar a garantia da entrega, outras, precisam de maior velocidade de forma que a retransmissão de algum segmento perdido inviabilize a comunicação

Desta forma, temos os protocolos TCP e UDP para atender as diferentes necessidades

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">Protocolo TCP (Transmission Control Protocol)</mark>

O TCP é um protocolo orientado à conexão (circuito virtual), descrito na RFC 793. O TCP possui um cabeçalho maior que permite adicionar as funções de entrega ordenada, entrega confiável e controle de fluxo.

Cada segmento TCP tem 20 bytes de overhead (cabeçalho) que encapsula os dados da camada de Aplicação, enquanto que o segmento UDP tem apenas 8 bytes.

As principais aplicações que usam TCP são:

* Navegadores web (HTTP)&#x20;
* E-mail (SMTP, POP, IMAP)&#x20;
* FTP
* SSH
* TELNET&#x20;
* RDP

### <mark style="color:red;">Solicitação TCP</mark>

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Three Way Handshake</mark>

Quando dois hosts se comunicam usando o TCP, uma conexão é estabelecida antes que os dados possam ser trocados (circuito virtual). Depois da comunicação ter sido completada, as sessões são fechadas e a conexão é encerrada.

> Os mecanismos de conexão e sessão possibilitam a confiabilidade dos dados trafegados.

Os Bits de controle no cabeçalho TCP indicam o progresso e o status da conexão (Three Way Handshake, ou handshake triplo):

* Determina que o dispositivo de destino está presente na rede;
* Verifica se o dispositivo de destino tem um serviço ativo e está aceitando solicitações no número de porta que o cliente deseja se conectar;&#x20;
* Informa o dispositivo de destino que o cliente de origem pretende estabelecer uma sessão de comunicação na porta especificada

Para entender o processo, é importante examinar os vários valores que os dois hosts trocam. Dentro do cabeçalho TCP, existem seis campos de 1 bit que contêm a informação de controle usada para gerenciar os processos TCP. Esses campos são:&#x20;

URG – Indicador de urgência (atualmente não é aplicado);&#x20;

<mark style="color:yellow;">ACK – Acknowledgement (Campo de confirmação);</mark>&#x20;

PSH – Função Push; • RST – Resetar a conexão;&#x20;

<mark style="color:yellow;">SYN – Sincronizar números de sequência (Pedido para iniciar uma conexão);</mark>&#x20;

<mark style="color:yellow;">FIN – Não há mais dados do remetente (Pedido para finalizar uma conexão);</mark>

{% hint style="info" %}
OBS.: Os principais neste processo estão marcados de amarelo
{% endhint %}

Estes campos são referidos como “flags”, porque cada campo possui apenas 1 bit, portanto, tem apenas dois valores: 1 ou 0.

Quando um valor de bit é definido como 1, a “flag” está ativada

Estas “flags” possibilitam iniciar ou encerrar uma conexão (circuito virtual)

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:yellow;">Estabelecendo conexão</mark>

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:yellow;">Finalizando conexão</mark>

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:red;">TCP State Machine: (Máquina de Estados TCP)</mark>

Esta imagem representa todo o processo de comunicação do protocolo TCP, descrevendo a sequência de estados TCP, no cliente e no servidor, desde o início ao final de uma conexão (circuito virtual).

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">Protocolo UDP (User Datagram Protocol)</mark>

O UDP é um protocolo simples e sem conexão, descrito na RFC 768. Ele tem a vantagem de fornecer uma entrega de dados com baixo overhead.

Os segmentos de comunicação em UDP são chamados datagramas. Estes datagramas são enviados como o "melhor esforço" por este protocolo da camada de Transporte.

As principais aplicações que usam UDP incluem:&#x20;

* Domain Name System (DNS)
* Simple Network Management Protocol (SNMP)&#x20;
* Protocolo de Configuração Dinâmica de Host (DHCP)&#x20;
* Routing Information Protocol (RIP) • Trivial File Transfer Protocol (TFTP)&#x20;
* Jogos On-line&#x20;
* Vídeo em Streaming (em alguns casos)&#x20;
* Voz Sobre IP (VOIP)

O UDP é um protocolo simples que fornece as funções básicas da camada de Transporte. Ele possui overhead muito mais baixo do que o TCP, já que não é orientado à conexão e não fornece mecanismos de retransmissão, sequenciamento e controle de fluxo sofisticados.

Isto não significa que as aplicações que usam UDP sejam de baixa qualidade ou confiabilidade. Isto simplesmente significa que estas funções não são fornecidas pelo protocolo da camada de Transporte e devem ser implementadas em outros locais se houver necessidade (Aplicação).

***

## <mark style="color:red;">Comparativo entre os protocolos TCP e UDP</mark>

Basicamente, as diferenças entre os Protocolos da camada de transporte (TCP e UDP), são:

* A garantia de entrega através do “Ack” (Acknowledgement) e retransmissão (caso ocorra perda de segmentos);
* Sequenciamento;&#x20;
* Controle de fluxo;&#x20;
* Protocolo orientado a conexão.

Ambas características citadas acima são do Protocolo TCP. Portanto, não temos o estabelecimento de um “circuito virtual” (VC) com o protocolo UDP

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Cabeçalho dos Protocolos TCP e UDP</mark>

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Endereçamento de porta</mark>

Para diferenciar os segmentos e datagramas de cada aplicação, o TCP e o UDP têm campos de cabeçalho que podem identificar unicamente essas aplicações. Estes identificadores únicos são os números de porta.

No cliente, uma porta aleatória acima de 1023 é designada para estabelecer a conexão (open ativo).

> _Também conhecida como "ephemeral ports", os clientes utilizam um range (intervalo) pré-definido no sistema operacional. Versões antigas do Windows e do GNU/Linux, utilizam portas a partir de 1024. Versões recentes do Windows (a partir do Vista) utilizam o intervalo recomendado pelo IANA (de 49152 a 65535), já versões recentes do GNU/Linux utilizam o intervalo (de 32768 a 60999)._

No servidor, temos portas específicas abertas para cada serviço (open passivo)

Por exemplo, uma solicitação de página HTTP sendo enviada a um servidor web (porta 80) sendo executado em um host com um endereço de IPv4 Camada 3 192.168.1.20 seria destinado ao SOCKET 192.168.1.20:80.

A Internet Assigned Numbers Authority (IANA) designa números de porta. A IANA é um órgão de padrões responsável pela designação de vários padrões de endereçamento.

{% embed url="http://www.iana.org/assignments/port-numbers" %}

Também podemos acessar o arquivo “services” no Windows ou Linux para visualizar esta listagem de portas.

* Windows: Arquivo “services” em “C:\WINDOWS\system32\drivers\etc\”.&#x20;
* Linux: Arquivo “services” no diretório “/etc”.

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Comando “netstat” e “ss”</mark>

Através do comando `netstat` podemos visualizar:&#x20;

* As portas abertas (serviços de rede aguardando solicitações) no computador;&#x20;
* Conexões TCP sendo estabelecidas, já estabelecidas ou sendo encerradas.

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**OBS.:** Preferencialmente, utilize os parâmetros “–n” (para não resolver nomes) e o “–a” (para exibir todas as portas abertas, ao invés de exibir somente as conexões existentes no momento).
{% endhint %}

> _Uma dica é que podemos saber quem é o servidor pois temos a mesma porta (22 TCP) no estado LISTEM (além de ESTABLISHED)_

***
