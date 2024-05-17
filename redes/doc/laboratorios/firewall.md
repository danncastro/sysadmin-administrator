# Firewall

Caso você queira criar uma instância Amazon EC2 semelhante ao que o instrutor está utilizando no curso, siga esse passo a passo.

Criando a instância Primeiramente, clique em Services, no menu superior da página, à esquerda. Em Compute, clique em EC2:

Você pode selecionar a região de São Paulo, também no menu superior, à direita:

No menu da esquerda, dentro de INSTANCES, clique no submenu Instances. Logo após, clique em Launch Instance:

No passo 1 (Choose an Amazon Machine Image (AMI)), selecione Quick Start à esquerda. Na versão disponível de Amazon Linux AMI, clique em Select:

No passo 2 (Choose an Instance Type), selecione o tipo de instância t2.micro, é importante selecionar um tipo que esteja disponível para contas gratuitas, eles são identificados pela legenda Free tier eligible. Após selecionar, clique em Review and Launch:

Isso fará com que você vá para o passo 7 (Review Instance Launch), mas no menu superior, volte ao passo 6 (Configure Security Group). Adicione uma nova regra, clicando em Add Rule, o tipo será o HTTP, isso permitirá com que você possa acessar a instância utilizando o seu navegador. Após adicionar a regra, clique em Review and Launch:

Os passos anteriores são dispensáveis, mas você pode aumentar o tamanho do volume no passo 4, por exemplo. No passo 7, Clique em Launch (não se preocupe a respeito do aviso de segurança, afinal é isso que iremos mexer mais à frente):

Uma tela irá aparecer solicitando a criação de um key pair (par de chaves). Essa segurança é necessária, pois a key pair é a chave de acesso à instância EC2. Utilizando ela, você consegue se conectar à instância EC2 via SSH, mas ela também é utilizada para descriptografar a senha de Administrador do Windows. Se essa chave for apagada, não será possível acessar a instância. Logo, guarde bem essa chave e tenha controle de quem terá acesso e ela.

Para criar o par de chaves, selecione Create a new key pair, dê um nome a ela e clique em Download Key Pair. Após o download, você pode clicar em Launch Instances:

Configurando a instância Para se conectar à instância, a sua chave não deve ser vista publicamente para que o SSH funcione. Para isso rode este comando no terminal:

sudo chmod 400 NOME\_DA\_CHAVE.pem

No menu da esquerda, dentro de INSTANCES, no submenu Instances, você verá as suas instâncias criadas. Obtenha o Public DNS da sua instância para conseguir fazer o SSH:

ssh -i NOME\_DA\_CHAVE.pem ec2-user@PUBLIC\_DNS\_DA\_SUA\_INSTANCIA

Ao se conectar à instância, instale o Apache e o MySQL nela, executando os seguintes comandos (digite y para confirmar as instalações, caso seja perguntado):

sudo yum update sudo yum install httpd sudo yum install mysql-server

E para inicializar o Apache e o MySQL, execute:

sudo service httpd start sudo service mysqld start

Abra o DNS público no seu navegador digitando o publico, uma página deve ser exibida:

Dentro do firewall nativo da AWS, é importante aplicarmos corretamente as regras. Para tanto, é importante entendermos a sua nomenclatura. O que significa Inbound e Outbound?

Inbound - Tráfego que chega até o firewall em direção ao servidor/rede. Outbound - Tráfego originado no servidor/rede com destino a outras redes. Como se trata de um elemento de proteção, a referência é o lado que queremos proteger

Limitar os IPs que têm acesso de gerenciamento é uma boa prática de segurança. Dentro da criação das regras, no campo Source, quais são as opções para esse fim?

Custom e My IP. Através da opção My IP, você configura a regra com o IP que estiver fazendo acesso no momento. E na regra Custom você pode configurar intervalos de IPs que podem ter acesso.

Por default, para máquinas Linux é criado uma regra na AWS que permite acesso remoto ao seu servidor. Esta é configurada permitindo acesso à porta: 22 Ao criar um Security Group por default (máquinas Linux), é criada uma regra que permite que você faça a conexão através do protocolo SSH (porta 22).

Quais foram as boas práticas, usadas no vídeo, referentes à configuração do Firewall? Criar a regra mais especifico possível. Correto, sempre sendo mais específico possível.

Configurar regras especificas para Outbound e abrangentes para Inbound. Errado, é justamente contrários, o Inbound deve ser mais especifico possível.

Mudar a porta padrão do serviço, se for possível. Correto, para os serviços como SSH ou RDS é boa prática mudar a porta padrão

Colocar o IP da minha maquina para o serviços que gerenciam a maquina. Correto, para os serviços como SSH ou RDS é boa prática colocar a IP especifica que pode acessar o servidor.

Neste capítulo, veremos como instalar e configurar o pfSense. O próximo vídeo mostra os detalhes da configuração do pfSense e, para acompanhar melhor, seguem os passos preparativos.

Ambiente virtualizado Idealmente, você deve possuir mais dois computadores extras e um roteador para testar as configurações, mas se você não tem isso disponível, fique tranquilo pois mostramos a você como criar uma laboratório usando Virtualização. O nosso objetivo é criar um laboratório que simula o pfSense e um servidor, tudo no seu computador. Para tal vamos criar duas máquinas virtuais, uma para o pfSense e outra para um servidor que queremos proteger:

Para isso tudo funcionar o ideal é que você tenha no mínimo 8GB RAM e 20 GB livres no HD. Com essas maquinas virtuais podemos simular duas redes, uma interna e outra externa. O que queremos é proteger a rede interna (o servidor). Na imagem abaixo já tem mais detalhe sobre a configuração das IP's mas veremos todos os passos nesse e nos próximos exercícios:

Downloads do VirtualBox e pfSense Usaremos o VirtualBox para a virtualização. Para tal baixe o VirtualBox específico para a sua plataforma no seu site: www.virtualbox.org. Após o download, instale o VirtualBox em seu computador.

Criando uma nova máquina virtual Com o VirtualBox instalado, crie uma nova máquina, dê um nome a ela, selecione o tipo Linux e a versão Other Linux (32-bit) ou Other Linux (64-bit). Após isso, clique em Próximo (N) >:

Na tela seguinte, selecione o tamanho da memória. No próprio site do pfSense há a recomendação de 1 GB de memória. Logo, selecione 1024 (já que o valor está em MB) e clique em Próximo (N) >:

Crie um disco rígido virtual, selecionando a opção Criar um disco rígido virtual agora e clicando em Criar:

Na tela Tipo de arquivo de disco rígido, selecione a opção VDI (VirtualBox Disk Image) e clique em Próximo (N) >:

Na próxima tela, Armazenamento em disco rígido físico, selecione a opção Dinamicamente alocado e clique em Próximo (N) >:

Em Localização e tamanho do arquivo, dê um nome ao disco rígido virtual e selecione o seu tamanho, 8 GB é mais do que o suficiente. Após isso clique em Criar:

Agora a máquina virtual está criada:

Não instalamos o pfSense ainda, criamos apenas a sua máquina virtual.

A máquina virtual já está criada, mas falta configurá-la para depois instalar o pfSense, mas isso fica para o próximo exercício.

Download do pfSense Para instalar o pfSense, devemos associar a máquina virtual com o ISO de instalação do pfSense. Para tal baixe o ISO do pfSense - Escolha a mesma arquitetura da sua máquina virtual: 32 ou 64 bits; Selecione o Installer como DVD Image (ISO).

Configuração do armazenamento da máquina virtual Já temos a máquina virtual instalada e o ISO baixado, agora vamos ajustar algumas configurações. Selecione a VM pfSense e clique em Configurações:

Na tela que se abrir, selecione Armazenamento à esquerda. E dentro de Armazenamento, clique no item Vazio, que fica abaixo da controladora de disco ótico (um ícone de CD/DVD):

Feito isso, clique na seta ao lado do campo Drive de CD/DVD (também um ícone de CD/DVD). No menu que aparece, clique na opção Selecione um arquivo de CD/DVD virtual…:

Selecione a ISO do pfSense que você baixou e clique em Abrir.

Essa configuração faz que o ISO do pfSense seja lido ao iniciar a máquina virtual (como se fosse um CD/DVD no computador).

Configuração da rede da máquina virtual Ainda em Configurações, selecione Rede à esquerda. Habilite dois adaptadores, o primeiro será conectado à placa em modo Bridge. No campo nome, é importante selecionar a interface (placa) que recebe o sinal da internet no host:

E o segundo adaptador será conectado à rede interna:

Configuramos duas placas (interfaces) de rede que precisaremos para concluir a instalação do pfSense. Feito isso, feche as configurações.

Você já pode iniciar a máquina virtual, clicando em Iniciar (T). Ao inicializar a máquina virtual começará a instalação do pfSense, que veremos no vídeo! Até lá!

Vamos rever os passos da instalação apresentada no vídeo. Se você já instalou pfSense acompanhando o vídeo, pode pular este exercício.

Instalação do pfSense Caso não tenha feito ainda, clique em Iniciar (T) para subir a sua máquina virtual:

A partir daí, começa a instalação do pfSense e aparece um menu para definir formas de inicializar (Boot Multi-User ou Boot Single-User). Basta esperar o timeout para começar a instalação automaticamente:

Após um tempo, aparece outro menu com a possibilidade de usar o modo de recuperação, que não é o nosso desejo. Aqui também basta esperar o timeout para continuar:

No próximo menu, podemos configurar detalhes sobre placa de vídeo e teclado. Deixe as configurações padrões e selecione Accept these settings:

No próximo menu, podemos dizer se queremos personalizar o pfSense na hora de instalar. Como configuraremos os detalhes do pfSense após instalação, selecione Quick/Easy install :

A próxima tela é apenas a confirmação da tela anterior, selecione OK:

Logo depois, devemos confirmar o uso do Standard Kernel:

Por fim, reinicie a máquina selecionando a opção Reboot. Assim que a máquina for reiniciada, desligue-a, fechando a máquina virtual diretamente pelo VirtualBox.

Assim como foi feito para adicionar a ISO do pfSense, remova-a. Selecione a máquina virtual e clique em Configurações. Na tela que se abrir, selecione o item Armazenamento à esquerda. E dentro de Armazenamento, clique na ISO, e em seguida clique na seta ao lado do campo Drive de CD/DVD (um ícone de CD/DVD). No menu que aparece, clique na opção Remover disco do drive virtual:

Rode novamente a máquina virtual, o pfSense irá executar automaticamente (a primeira execução pode demorar um pouco). Assim que o boot terminar, irá aparecer um console de gerenciamento:

Uma vez instalado, podemos configurar os IPs (referentes aos adaptadores de rede que configuramos anteriormente), mas isso faremos no próximo exercício.

Vamos rever os passos da configuração apresentada no vídeo (IPs para WAN e LAN). Se você já configurou pfSense acompanhando o vídeo, pode pular este exercício.

Lembrando que é importante ter configurado os dois adaptadores na máquina virtual, o Adaptador 1 como Bridge e Adaptador 2 como Rede Interna. Neste exercício, vamos seguir as configurações apresentadas na imagem:

Configuração da IP do WAN O primeiro passo é alterar o IP da WAN (Rede Externa) para 192.168.1.200/24. No menu principal, digite a opção 2 (Set interface(s) IP address):

Depois disso, escolha 1 para WAN, digite n para não usar DHCP, e coloque o IP 192.168.1.200 com a mascará 24:

Depois disso, tecle ENTER para deixar o gateway em branco e digite n para desabilitar o DHCP. Também não defina nenhum endereço IPv6 (tecle ENTER). Como queremos acessar o pfSense pela interface web, digite y no item webConfigurator protocol. Por fim, tecle ENTER para confirmar:

Configuração da IP do LAN Repita agora os mesmos passos, mas para a LAN (Rede interna). Novamente no menu, digite a opção 2 (Set interface(s) IP address) e depois disso, escolha 2 para LAN, mas usando o IP 10.0.0.200/24, sem gateway, sem IPv6 e sem DHCP:

Resumo No menu principal devem aparecer os novos IPs da WAN e LAN:

Na imagem apresentada no vídeo, mostramos o acesso ao pfSense a partir de um server com o IP 10.0.0.100. Neste exercício vamos criar esse server usando VirtualBox e Ubuntu.

Download do Ubuntu Desktop Para simular o server, podemos utilizar o Ubuntu Desktop ou Lubuntu. Vamos utilizar essas distribuições para usar a interface gráfica, mas fique à vontade de usar uma outra distribuição ou outro sistema operacional.

Baixe a ISO do Ubuntu Desktop (64bit) aqui.

Criação da máquina virtual Como fizemos no primeiro exercício desse capítulo crie uma nova máquina virtual no VirtualBox, seguem as especificações:

Nome: Ubuntu Desktop, Tipo: Linux, Versão: Ubuntu (64-bit) Memória: 2048MB, Disco Rígido: VDI, Dinamicamente alocada, 10GB

Logo após a criação, selecione a máquina virtual e clique em Configurações, depois no item Rede\*. No Adaptador 1, escolha _Rede interna_\*

Uma vez criada a máquina virtual, você pode inicializá-la e logo em seguida o VirtualBox perguntará qual a imagem usar. Escolha a ISO do Ubuntu Desktop que baixou anteriormente e clique em Iniciar:

Instalação do Ubuntu A partir daí, comece todo o processo de instalação Ubuntu.

Seguem as especificações:

Idioma: Português do Brasil Sem baixar atualizações e pacotes de terceiros Apagar o disco e reinstalar Fuso horário: São Paulo Layout Teclado: escolha o seu Nome do usuário: server, senha: alura A instalação vai levar alguns minutos.

Configuração da rede no Ubuntu Após instalação você deve reiniciar o Ubuntu e ver a tela de login:

Clique na rede e depois em Editar conexões:

Após isso clique em Wired connection 1, clique em Editar, e selecione a aba Configurações IPv4:

Em Método, selecione Manual, e em Endereços, clique em Adicionar. Agora é a hora de configurar o IP, em Endereço digite 10.0.0.100, em Máscara de rede, digite 24 (referente à 255.255.255.0), em Gateway digite 10.0.0.200 e no campo abaixo, em Servidores DNS, digite 8.8.8.8 e 8.8.4.4, separados por vírgula:

Após isso clique em Salvar… e reconecte a rede.

Testando a comunicação Para testar a comunicação entre que o pfSense e o Ubuntu ambas as máquinas virtuais deve estar rodando. No Ubuntu, no terminal, use o comando ping para verificar a conexão:

ping 10.0.0.200

Repare que usamos o IP do pfSense:

Se o ping funcionou podemos acessar o pfSense a partir do Ubuntu usando um navegador. Abra um navegador e digite http://10.0.0.200:

Como apresentamos no video, seguem os passos para a configuração do pfSense a partir da interface web. O mais importante aqui é a configuração do Gateway. Só com Gateway configurado corretamente é possível acessar a internet a partir do Server (LAN).

Lembrando do nosso desenho:

Acesso pela web Garanta que ambas as máquinas virtuais estão rodando. A partir da máquina virtual Server, acesse o pfSense pelo navegador: http://10.0.0.200

Como usamos o IP interno do pfSense, uma tela de login é apresentada:

O login e senha padrões são admin e pfsense, respectivamente.

Hostname, Servidores DNS e NTP Nos próximos passos configure:

O seu hostname desejado Os servidores DNS do Google: 8.8.8.8 e 8.8.4.4 Time server hostname: a.ntp.br e com fuso horário America/Sao\_Paulo Adicionando o Gateway No item Static IP Configuration da WAN já temos o IP configurada anteriormente, agora vamos adicionar o Gateway. No nosso caso o Gateway utilizado é 192.168.1.1 mas é importante que você coloque o IP do seu Gateway.

É importante também é que você use o mesmo subnet. Por exemplo, se o seu Gateway possui o IP 192.168.0.1 (Subnet: 192.168.0.x), o IP da WAN deve ser também nesse padrão, logo 192.168.0.200.

Verifique as outras configurações e salve as alterações no pfSense e clique em Reload no final.

A qualquer momento você pode repetir os passos através do menu System -> Setup Wizard.

Testando Uma vez recarregada a configuração, você deve ter acesso à internet a partir do servidor. Você pode testar e diagnosticar a conectividade pelo terminal no servidor:

Testando a conectividade entre server e pfSense:

ping 10.0.0.200

ping 8.8.8.8

ping www.google.com

Durante o curso, nós usaremos o VirtualBox, que é uma plataforma open source capaz de gerenciar máquinas virtuais, com isso poderemos ter no nosso computador o Firewall (pfSense) e o servidor interno rodando simultaneamente, como na imagem abaixo:

Perceba que nosso Firewall (pfSense) precisa de duas interfaces, uma interface será conectada com a rede externa e a outra interface será conectada com a rede interna, junto com nosso servidor de endereço IP 10.0.0.100. Agora, como podemos configurar essas duas interfaces no VirtualBox?

O primeiro passo é clicar em Configurações, e depois no menu lateral esquerdo devemos clicar na opção Rede:

Perceba que ao clicar na opção Rede, nós teremos ao lado direito a parte de configuração dessas interfaces. Veja que em destaque na cor amarela, nós temos os adaptadores que podemos configurar para essa máquina virtual, que será o firewall (pfSense), esses adaptadores é que serão as nossas interfaces. Se nos lembrarmos do primeiro diagrama, precisamos de duas interfaces no nosso Firewall (pfSense), uma interface conectada com a rede externa (a internet) e outra interface conectada com a rede interna, com o servidor interno de endereço IP 10.0.0.100. Com isso, podemos configurar por exemplo o Adaptador 1 para ser a interface conectada à rede externa, a internet. Mas veja as opções que temos disponíveis para configurar esse adaptador, qual opção devemos escolher?

Lembre-se que as máquinas virtuais estão rodando no nosso computador, que está recebendo os dados de configuração de endereços IP vindo do servidor DHCP, que está configurado no nosso roteador doméstico, parecido com a imagem abaixo:

O nosso roteador é que fará a conexão com o modem do provedor de serviços que contratamos (NET, Telefonica, etc) e que nos conectará na internet. A conexão do nosso computador com o roteador poderá ser tanto de forma cabeada como de forma sem fio (wireless).

Uma vez que o nosso computador está realizando essa conexão com o roteador e a internet, nós precisamos estender essa conexão para que nosso Adaptador 1, que será a interface do Firewall (pfSense) conectada com a rede externa, também acesse a internet, essa extensão seria uma espécie de “ponte” que temos que criar entre a placa de rede do nosso computador com a placa de rede da máquina virtual do Firewall (pfSense). Com essa extensão, nossa máquina virtual também estará apta a se comunicar com a internet, a ideia da configuração seria essa:

Se voltarmos na análise das opções possíveis de serem selecionadas, nós temos a opção de conectar a placa da rede da nossa máquina virtual Firewall (pfSense) em modo Bridge (Ponte):

Feito essa configuração, nós precisamos especificar qual é a placa de rede do nosso computador que está conectada à internet, que queremos fazer essa Bridge (Ponte). No meu caso estou usando a conexão Wireless do meu computador para conexão com a internet, então irei escolher essa opção:

A configuração da interface conectada com a rede externa, a internet foi realizada. Agora precisamos configurar a interface interna, que será conectada com o servidor interno de endereço IP 10.0.0.100, essa interface interna será o Adaptador 2:

Não podemos nos esquecer que essa máquina virtual está rodando no nosso computador e que nosso intuito é agora isolar essa rede interna, que irá conter o servidor interno com endereço IP 10.0.0.100, da rede modo Bridge que realizamos antes. Para isso, esse nosso Adaptador 2 deverá atuar em um outro modo, chamado de rede interna, ou em inglês Internal Network:

Com essa configuração, estaremos isolando a rede do Adaptador 2 da rede do Adaptador 1, e a configuração do nosso Firewall (pfSense) está concluída.

Para finalizar, nós precisamos configurar também nosso servidor interno com endereço IP 10.0.0.100 para que ele fique na mesma rede do Adaptador 2 do Firewall (pfSense). Devemos seguir os mesmos passos anteriores, clicamos em Configurações e depois no menu lateral esquerdo nós clicamos em Rede:

O servidor interno tem por sua vez somente uma interface, que deverá estar presente na mesma rede do Adaptador 2 do Firewall (pfSense). Para que ambos estejam na mesma rede, devemos configurar a placa de rede do servidor interno para que também atue no modo de rede interna, ou em inglês, Internal Network.

Para podermos testar uma regra INBOUD falta ter um serviço rodando no nosso servidor interno. A nossa ideia é que o servidor interno roda um servidor web que deve ser acessível pela rede interna.

Para testar essa configuração falta instalar esse servidor. Como usamos Ubuntu isso é muito fácil de fazer, basta instalar o servidor Apache2. Para tal:

1. No Ubuntu abra um terminal e digite: sudo apt-get update
2. Depois digite a senha. Isso atualiza o lista de pacotes disponíveis. Uma vez atualizada a lista execute ainda no terminal: sudo apt-get install apache2 3)Isso baixará e instalará o servidor apache2 no ubuntu. Por fim, para garantir que o servidor está rodando digite no terminal: sudo service apache2 start
3. Logo após instalação abra o navegador Firefox e acesse: http://localhost Você deve ver a página inicial do servidor apache (e isso é a prova que o apache está rodando):
4. Opcional: Como Apache está rodando e acessível pelo protocolo HTTP, automaticamente foi aberto uma porta para possibilitar a conexão via rede. Você pode testar o comando netstat para ver a porta no estado listening (ou Ouça):
5. Resumindo, temos o pfSense e o Servidor interno rodando, ambos em ambiente virtualizado. Agora queremos testar o acesso OUTBOUND, ou seja, a partir de uma terceira maquina queremos acessar o apache2 através do protocolo HTTP. Isso significa que precisamos passar pelo pfSense:

Ambiente Nesse capitulo, vamos focar no iptables sem pfSense. Isso também significa que o ambiente ficará mais simples. Se você já é usuário Linux, saiba que você já é apto para continuar com o curso, sem necessidade de fazer este exercício.

Se você é usuário Mac ou Windows, é preciso criar uma máquina virtual com Linux para reproduzir o conteúdo da aula:

Configuração Seguem os passos de configuração:

1. Se você já criou uma máquina virtual para rodar o Ubuntu na aula 2, você precisa alterar apenas a configuração da rede da máquina virtual. Se quiser guardar a máquina virtual, você pode cloná-la, mas primeiramente desligue a máquina virtual (Power off).
2. (Opcional) Se quiser clonar a máquina virtual, selecione o Ubuntu, clique com o botão direito do mouse, e clique em Clonar (Clone completo). O VirtualBox fará uma cópia que pode demorar alguns minutos:

Novamente, você não precisa clonar e pode utilizar a máquina virtual original.

3. Depois, selecione a máquina virtual clonada e clique no botão Configurações:
4. Depois, vá à aba Rede e selecione Bridge no Adaptador 1:
5.
   4. A configuração Bridge faz que a máquina virtual possua o sua IP na rede. Basta agora você descobrir esse IP. Para tal, inicie a máquina virtual clonada e efetue o login. Após o login, abra um terminal e digite o comando ifconfig:

Repare que no caso da configuração na imagem, o IP (inet end) é 192.168.0.138.

Sabendo esse endereço, podemos acessar o servidor Apache.

5. Temos o servidor Apache2 rodando no Ubuntu. Ele automaticamente deve estar rodando, mas caso não esteja digite no terminal:

sudo service apache2 start

Agora você pode testar o acesso à máquina virtual a partir do navegador do seu computador. Abre o Chrome/Firefox e digite o IP da máquina virtual, no caso desse exercício:

http://192.168.0.138

Na imagem abaixo, estamos mostrando o acesso ao Apache fora e dentro de máquina virtual. Fora, estamos usando o IP, dentro estamos usando localhost para acessar o Apache2:

6. Agora que temos um serviço (Apache2) desprotegido, você pode continuar assistindo o próximo vídeo. Boa aula!

ATENÇÃO: A versão 8 do Tomcat está obsoleta, e no momento, essa versão já não consta mais no repositório do apt. Para funcionar é necessário fazer a instalação da versão 9.

Agora é a sua vez, vamos testar duas regras, uma ACCEPT e DROP, mas antes disso, vamos instalar um outro servidor HTTP, que roda na porta 8080. Para tal, execute no terminal:

sudo apt-get update sudo apt-get install tomcat9 sudo service tomcat9 start

Isso faz com que o servidor Tomcat seja iniciado, rodando por padrão na porta 8080.

Você pode testar o Tomcat, acessando no navegador http://localhost:8080

Testando as regras Agora está com você, crie uma regra para aceitar chamadas TCP na porta 80, e negar chamadas TCP na porta 8080:

Política: ACCEPT Chain: INPUT Destino: IP da sua maquina virtual linux Porta: 80

Política: DROP Chain: INPUT Destino: IP da sua maquina virtual linux Porta: 8080

Seguem as duas regras a executar: iptables -A INPUT -p tcp -d IPDAMAQUINA --dport 80 ACCEPT iptables -A INPUT -p tcp -d IPDAMAQUINA --dport 8080 DROP

Em outras palavras, continuamos com o acesso ao Apache2 (HTTP/80) mas não podemos acessar o Tomcat (HTTP/8080).

Partindo do princípio que há um servidor web, banco de dados, entre outras aplicações, tudo funcionando na mesma máquina, quando o servidor web consulta o banco de dados, por exemplo, o IP de origem não é o IP associado à interface ethernet, e sim o IP da interface loopback.

Por isso, deve-se criar uma regra para permitir essas conexões internas do servidor. Se não houver uma regra desse tipo no firewall, as conexões internas na mesma máquina não irão funcionar.

No momento de criar a regra, para permitir qualquer origem ou destino, basta não especificá-los. Além disso, passa-se a flag -i (de interface) e especifica-se a interface lo (de loopback):

iptables -A INPUT -i lo -j ACCEPT

A ferramenta é o iptables-save, ela nos retorna tudo o que estiver rodando na memória (regras e políticas, por exemplo). Então, podemos salvar isso em um arquivo, por exemplo:

iptables-save > regras-firewall

E com outra ferramenta, a partir desse arquivo, podemos carregar as regras e aplicá-las em memória. Essa ferramenta é a iptables-restore:

iptables-restore < regras-firewall
