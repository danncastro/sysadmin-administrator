# Segurança

Quais são algumas das limitações que possuímos no uso dos hubs? Os hubs não conseguem “aprender” qual equipamento está conectado em cada porta. Dessa forma, ele repassa a informação para todas as suas portas, causando uma lentidão em nossa rede, assim como uma potencial vulnerabilidade de segurança visto que um usuário mal-intencionado poderá fazer o uso de análises de protocolos de rede para decifrar o que uma possível vítima estava acessando.

Qual seria uma das formas mais efetivas que um hacker pode vir a comprometer o funcionamento de um switch?

Uma das formas seria "lotar" a memória do switch com uma grande quantidade de endereços mac. Uma vez que a memória do switch esteja cheia, o switch não conseguirá mais distinguir quem está conectado em cada porta e passa a atuar como um hub.

O hacker pode vir a comprometer o funcionamento de um switch ao "lotar" essa memória com uma série de endereços mac. Uma vez que essa memória está cheia, o Switch não consegue distinguir que máquina está conectada em cada porta e dessa forma, ele passará a atuar como se fosse um hub.

Abra o GNS3 e caso o programa pergunte se desejamos configurar um servidor, clique no botão Cancel. Salve o nome do projeto como Switch. Na aba lateral esquerda:

Clique no segundo ícone e arraste o Switch para a área de trabalho Clique no terceiro ícone e arraste para área de trabalho o ícone Host. Clique no terceiro ícone e arraste para a área de trabalho dois ícones VPCS que serão os computadores virtuais do GNS3. Clique no sexto ícone, dos cabos e conecte os computadores em uma entrada do Switch. No ícone host, escolha a placa de rede do VirtualBox. O resultado final deverá estar parecido com a imagem abaixo:

Em seguida, clique no botão verde Start. Feito isso, todas as portas deverão estar com a cor verde. Na sequência, clique no botão de Console que está ao lado do botão de Start. Vá ao VirtualBox, inicialize o Kali Linux Abra o terminal no Kali Linux e verifique o endereço IP através do comando ifconfig. Por exemplo:

Para que os equipamentos possam se comunicar, eles precisam estar na mesma rede. Configure o PC1 e PC2 para estarem na mesma rede do Kali Linux, usando a seguinte comando: ip \[endereço IP] \[máscara de rede]. Por exemplo:

Ao configurar os endereços IP nos dois computadores virtuais, faça um PING contínuo entre eles através do comando ping \[IP] -t.

Clique com o botão direito do mouse no link conectado ao Hacker, e selecione a opção Start Capture.

Vá até o terminal do Kali Linux e realize o ataque para "lotar a memória" do Switch através do comando macof -i \[interface]. No Wireshark, coloque um filtro para ver a comunicação entre os outros dispositivos: ip.addr==\[endereço IP de um dos VPCS]. Qual o resultado?

Uma vez que realizamos o ataque para lotar a memória do Switch, fazemos com que ele se comporte como um Hub. Ao realizar o filtro, somos capazes de visualizar a comunicação entre os outros dois dispositivos.

O que consiste o ataque Man In the Middle (MITM)? O ataque consiste em manipular a tabela ARP de dispositivios para que o Hacker fique assim no meio da comunicação e possa visualizar o O ataque Man In The Middle consiste em explorar a forma sem estado (stateless) na qual o protocolo ARP trabalha. Dessa forma, um Hacker pode usar de ferramentas para enviar respostas desse protocolo com o intuito de manipular a tabela ARP de suas vítimas para ficar assim no meio da comunicação e visualizar o que é trafegado entre os dispositivos manipulados.

O que consiste o ataque de DNS Spoofing? O ataque de DNS Spoofing consiste em alterar a tradução entre URL e endereço IP para que essa url seja redirecionada a um endereço IP de controle do Hacker. O ataque de DNS Spoofing consiste em alterar a tradução da URL para um endereço IP que seja de domínio do Hacker.

O que consiste o ataque DOS? O ataque consiste em um usuário que utiliza de formas para consumir os recursos de um serviço (por exemplo, abrir várias conexões) com o objetivo assim de tornar o serviços indisponível para outros usuários.

Um ataque de negação de serviço ou em inglês Denial Of Service (DoS) ocorre quando temos um usuário que utiliza de recursos para causar uma sobrecarga em um sistema com o principal objetivo de torná-lo indisponível para outros usuários.

Parabéns, você acertou!

Quais são algumas formas nas quais as redes corporativas podem tentar se proteger de ataques de DoS?

Poderíamos ter equipamentos na rede que fazem detecção de possíveis ataques como o Intrusion Detection System (IDS) ou prevenção desses ataques como o Intrusion Prevention System (IPS).

As redes corporativas possuem alguns equipamentos com o objetivo de verificar o tipo de tráfego que é enviado por seus usuários e caso esse tráfego represente algum possível ataque, que alguma medida seja tomada para evitar que esse ataque se propague.

Equipamentos que temos nas redes são por exemplo o Intrusion Detection System (IDS) que recebe cópias desse tráfego e caso alguma anomalia seja detectada, o equipamento manda alarmes para que assim os administradores da rede possam saber o ocorrido e procurar uma solução. Outra solução seria a utilização de equipamentos como o Intrusion Prevention System (IPS) que é capaz de detectar anomalias no tráfego e impedir que esse tráfego seja propagado para outros pontos da rede.

Qual seria uma diferença entre o Intrusion Detection System (IDS) e o Intrusion Prevention System (IPS)?

O Intrusion Detection System é capaz de detectar o ataque mas não impedí-lo como o IPS é capaz de fazer.

O Intrusion Detection System (IDS) recebe apenas cópias dos tráfego, dessa forma, ele não é capaz de impedir que um ataque seja propagado para outros pontos da nossa rede. Ele irá encaminhar alarmes para que possamos assim saber dos problemas que foram detectados e encontrar soluções.

O Intrusion Prevention System (IPS) é conectado diretamente na rede, dessa forma, ao analisar algum tipo de anomalia o IPS é capaz de impedir que esse tráfego seja propagado para outros pontos da minha rede.

Trabalhamos no ramo de vendas de um grande fabricante de equipamentos de rede e fizemos uma visita em uma empresa do ramo financeiro para mostrar nossas soluções. Durante a visita, o diretor técnico nos informou que para eles seria muito importante ter um equipamento que possa garantir uma maior segurança de sua rede e seus servidores web. Ele nos informou que por ser uma empresa do ramo financeiro, uma queda em um link seria muito prejudicial e deseja que nosso equipamento não interfira diretamente na rede. Sabendo disso, qual equipamento podemos oferecer inicialmente e porque?

Nesse cenário, parece que o IDS seja a melhor solução porque ele recebe somente cópias do tráfego e não é conectado diretamente na rede.

Uma vez que o diretor técnico nos informou que uma queda no link é muito prejudicial, podemos oferecer inicialmente a solução do Intrusion Detection System (IDS). Isso porque o IDS não é conectado em linha (in-line) com a rede e se tivermos algum tipo de reparo que seja necessário, não terá impacto na rede do cliente.

Ao mesmo tempo, o IDS recebe cópias do tráfego e com isso caso alguma anomalia seja detectada, poderá enviar alarmes para os administradores da rede para que seja possível assim encontrar uma solução para os problemas detectados.

Obs: Embora muitas vezes o IPS possa ser a melhor opção, existem cenários que o IDS pode atender melhor a necessidade do cliente. Quem no fim vai pesar as vantagens e desvantagens é o cliente.

O que consiste um ataque DDoS?

O ataque de DDoS consiste em distribuir o ataque entre vários usuários. Uma vez que várias máquinas estão realizando a comunicação com tal serviço, é possível que ocorra um comprometimento desse serviço (por exemplo, saturando o link) tornando-o assim indisponível.

O ataque DDoS (Distributed Denial of Service) consiste em tirar a concentração do ataque em um usuário, como é feito no ataque de DoS e distribuir o ataque por vários usuários. Isso pode ser obtido por exemplo quando usuários fazem download de arquivos infectados. Uma vez que tais máquinas foram infectadas, o Hacker poderá controlá-las para que possa assim iniciar um ataque distribuído contra um serviço. O objetivo de tal ataque seria de causar uma "saturação" no link do alvo e com isso torná-lo indisponível para que outros usuários acessem o serviço.

O que são as chamadas Botnets em um ataque DDoS?

Botnets é um termo usado para referenciar máquinas que foram infectadas e podem ser assim usadas para realizar um ataque.

Uma botnet é um grupo de máquinas que foram comprometidas de alguma forma (por exemplo vírus, malware, etc). Tais máquinas infectadas passam a ser usadas por hackers para fazerem ataques contra um determinado serviço a fim de torná-lo indisponível. Pelo fato de termos várias máquinas atuando nesse ataque, chamamos esse de um ataque de negação de serviços distribuído (DDoS).

O DDos é um dos ataques mais comuns e também um dos mais temidos por organizações, uma vez que torna-se difícil a identificação dos dispositivos envolvidos e sua prevenção. Segue abaixo os links mostrados das reportagens dos atques DDoS:

https://krebsonsecurity.com/2016/11/new-mirai-worm-knocks-900k-germans-offline/ http://www.ibtimes.co.uk/anonymous-hacktivists-launch-ddos-attacks-against-websites-donald-trump-1552750

Qual seria a função dos firewalls em uma rede?

O firewall serve para dividir uma rede segura (rede interna) e uma rede não segura (por exemplo, internet), controlando o tráfego entre as redes com uma política de acesso.

O firewall é usado para dividir uma rede segura (rede interna) de uma rede não segura(por exemplo, a internet) e podemos assim controlar o tráfego que é permitido ou negado entre a rede interna e a rede externa. De forma geral, um usuário que esteja na rede interna poderá acessar recursos que estão na rede externa, porém um usuário da rede externa não terá permissão de acessar recursos da rede interna.

O que seria a região desmilitarizada (DMZ)?

A região DMZ é aquela na qual contém recursos de nossa rede que devem ser acessados por usuários externos.

A região desmilitarizada seria a região na qual temos recursos que devem ser acessados por usuários da internet. Dessa forma, conseguimos isolar essa região de recursos que precisam ser acessados externamente dos recursos que devem ser acessados somente por usuários de nossa rede interna.

Como é possível que um firewall com memória Stateful permita um pacote externo de acessar recursos internos da rede?

O firewall com memória stateful é capaz de analisar a requisição que foi realizada, endereços IP, portas de comunicação, etc. Dessa forma, quando for retornado um pacote de resposta a essa requisição, o firewall poderá comparar os dados chegados com os que possui na tabela e assim poderá perceber que trata-se de um retorno a uma requisição e permitirá o acesso.

Os firewalls stateful conseguem guardar em sua memória informações das requisições internas que foram iniciadas. Quando ocorre um retorno desse pacote o firewall compara com sua tabela de memória elementos como endereço IP, portas de comunicação, etc e com isso consegue definir que trata-se de uma informação de retorno e com isso permitirá acesso a rede interna.

O que seria um Reverse Shell e porque ele seria importante em um ataque?

O Reverse Shell seria a forma na qual a máquina alvo conecta-se com a máquina de ataque, fazendo com que o Hacker ganhe acesso a máquina. Esse ataque torna-se útil, pois é possível que equipamentos de segurança conceda permissão de acesso, uma vez que poderia ser interpretado como sendo um retorno a uma requisição.

O Reverse Shell seria a forma na qual o comando de uma máquina é obtida através de uma conexão da máquina alvo com a máquina de ataque. Ou seja, a conexão é estabelecida na direção reversa ao qual o ataque é realizada.

Esse tipo de ataque torna-se muito útil, pois é possível que equipamentos de segurança como o Firewall nos conceda permissão de acesso a rede interna uma vez que nosso pacote é um retorno a uma requisição que foi originada por um usuário interno a rede.

Qual seria uma das formas mais simples e efetivas de se obter um Reverse Shell?

Uma das formas seria criar um arquivo infectado e mandarmos um link ou e-mail para vítima de uma forma que ela seja convencida por meios da engenharia social a realizar o download do link. Ao realizar o download e executar o arquivo, iniciaria a conexão com a máquina de ataque formando um Reverse Shell

Uma das formas de se obter um Reverse Shell seria da vítima clicar em um arquivo malicioso criado por um Hacker e através desse arquivo malicioso ocorrerá uma conexão de reversa com a máquina de ataque.

Tais arquivos podem ser criados por exemplo com o msfvenom, onde podemos especificar o sistema operacional da vitima e como queremos realizar o ataque.
