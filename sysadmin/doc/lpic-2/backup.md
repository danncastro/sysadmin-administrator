# Backup

```
COMANDOS DE VISUALIZAÇÃO E LISTAGEM


echo
Usado para exibir a saída no terminal.
•	echo ~~ sysadmin ~ root ~ mail ~ arquivo or diretorio.
◦	Exibe o caminho absoluto ate o arquivo ou diretorio especificado.

cat
Abreviação de concatenar, é um comando simples, mas útil, cujas funções incluem criar e exibir arquivos de texto, além de combinar cópias de arquivos de texto.
•	Exibe todo o conteudo do arquivo.
◦	Por isso e recomendado para arquivos menores, onde a saida e limitada e não requer rolagem.
◦	Embora o terminal seja a saída padrão deste comando, o comando cat também pode ser usado para redirecionar o conteúdo do arquivo para outros arquivos ou inserir outro comando usando caracteres de redirecionamento.
▪	Sua sintaxe e a seguinte:
•	(cat TEXTO.txt).

less
O comando  less fornece um recurso de paginação muito avançado.
•	Geralmente é o pager padrão usado por comandos como o comando man.
•	Sua sintaxe e a seguinte:
◦	(less Nome_do_arquivo)
•	Teclas h ou Shift + H exibe uma tela de ajuda.
•	As teclas que são idênticas (more e less) estão resumidas abaixo para demonstrar como entrar (more e less) ao mesmo tempo:
◦	 Chave	                		Movimento
▪	Barra de espaço	      	Janela para a frente
▪	B	                    		Janela para trás
▪	Entrar	                		Linha em frente
▪	Q	                    		Saída
▪	H	                   		Socorro
▪	#                       		Número de linhas contadas na parte inferior da saída a serem excluídas.
•	Ao usar less como pager, a maneira mais fácil de avançar uma página é pressionar a barra de espaço .
•	Existem duas maneiras de pesquisar no comando less:
◦	Pesquisar para frente ou para trás a partir da sua posição atual.
▪	Para iniciar uma pesquisa a partir da sua posição atual, use a tecla barra (/).
•	Em seguida, digite o texto ou padrão correspondente e pressione a tecla Enter 	
◦	Se nenhuma correspondência a partir de sua posição atual puder ser encontrada, a última linha da tela informará
▪	Pattern not found:.
▪	Para pesquisar para trás em sua posição atual, pressione o ponto de interrogação (?), digite o texto ou padrão correspondente e pressione a tecla Enter.
•	Se mais de uma correspondência puder ser encontrada por uma pesquisa, use a tecla (n) para mover a próxima correspondência e use a combinação de teclas (Shift + N) para ir para uma correspondência anterior

more
O comando more existe desde os primeiros dias do UNIX.
•	O comando more está sempre disponível, direfente do comando less que nao esta presente em todas as distribuicoes, porem possui mais recursos que o comando more.


head
Utilizado para visualizar um numero selecionado de linhas na parte superior de um arquivo.
•	Sua sintaxe e a seguinte:
◦	head [OPCOES] [ARQUIVO]
◦	Por padrao este comando exibe apenas dez linhas no shell.
◦	Passar um número como uma opção fará com que o comando head produza o número especificado de linhas, em vez do padrão dez.
▪	Por exemplo:
•	Para exibir as últimas cinco linhas do arquivo (/etc/sysctl.conf), use a  opcao -5:
◦	(head -5 /etc/sysctl.conf)
•	A versão GNU do comando head reconhece -n -3 como mostrar todas, exceto as últimas três linhas, e ainda assim o comando head ainda reconhece a opção -3 como mostrar as três primeiras linhas.
•	
▪	Opcoes mais utilizadas:
•	Opcoes:	Significado:
◦	-n		Usada para especificar a quantidade de linhas a serem exibidas
▪	Por exemplo:
•	(head -n 3 /etc/sysct1.conf)
n1
Adiciona numeros de linha a saida.

tail
Utilizado para visualizar um numero selecionado de linhas na parte inferior de um arquivo.
•	Sua sintaxe e a seguinte:
◦	tail [OPCOES] [ARQUIVO]
◦	Por padrao este comando exibe apenas dez linhas no shell.
◦	Opção de valor negativo
▪	Para o comando tail, um -3 ou -n -3 ainda significa mostrar três linhas.
•	A versão GNU do comando tail permite uma variação de como especificar o número de linhas a serem impressas.
•	Se a opção -n for usada com um número prefixado pelo sinal de mais, o comando tail reconhecerá que isso significa exibir o conteúdo iniciando na linha especificada e continuando até o final.
◦	Por exemplo,
▪	(n1 /etc/passwd | tail -n +25)
•	O seguinte exibe o conteúdo da linha de origem (/etc/passwd) até o final do arquivo 25:
▪	Opcoes mais utilizadas:
•	Opcoes:	Significado:
◦	-n		Usada para especificar a quantidade de linhas a serem exibidas
◦	-f		Usada para visualizar as alteracoes do arquivo ativo.
▪	útil quando se deseja ver as alterações em um arquivo enquanto elas estão acontecendo.

ls
Usado para listar diretorios de arquivos.
•	Em muitas distribuições Linux, o comando (ls) usa cores para distinguir por tipo.
◦	Exemplos:
▪	Azul = Arquivos de Diretorios.
▪	Verde = Arquivos de Execucao
•	Um programa.
▪	Ciano = Links Simbolicos.
•	Um arquivo que aponta para outro arquivo.
▪	Preto ou branco = Arquivos regulares
•	Opcoes mais comuns no comando (ls):
◦	-a	Exibe todos os arquivos do diretorio, incluindo os arquivos ocultos.
◦	Arquivos ocultos:
▪	Um arquivo oculto é qualquer arquivo (ou diretório) que começa com um caractere de ponto (.arquivo)
•	Por exemplo, o arquivo “.bashrc” mostrado no exemplo
◦	(sysadmin@localhost:~$ ls -a).
▪	 Contém informações de configuração para o shell “bash.”
▪	Este é um arquivo que você normalmente não precisa visualizar regularmente.
◦	-h	Deixa legivel para humanos.
◦	-d	Refere-se ao diretorio atual.
◦	Esse comando deve ser usado junto a opcao (-l)
◦	-S	Classificar os arquivos por tamanho do maior para o menor.
◦	 A letra (S) e (maiusculo).
◦	-t	Classifica os arquivos com base na hora em que foram modificados.
◦	É importante lembrar que a data modificada nos diretórios representa a última vez que um arquivo foi adicionado ou removido do diretório.
▪	Para obter informações mais detalhadas sobre o tempo de modificação, pode-se usar a opção:
•	--full-time	Para exibir o registro de data e hora completo
◦	Incluindo:
▪	Horas, minutos, segundos.
◦	-R	Mostra o conteudo dos subdiretorios alem do atual
◦	(R) e (Maiusculo).
▪	Listagem recursiva:
•	Exibir todos os arquivos em um diretório, bem como todos os arquivos em todos os subdiretórios desse diretório.
◦	Tenha cuidado com esta opção;
▪	Por exemplo, executar o comando no diretório raiz listaria todos os arquivos no sistema de arquivos, incluindo todos os arquivos em qualquer dispositivo USB conectado e DVD no sistema.
◦	Limite o uso de listagens recursivas para estruturas de diretório menores.
◦	-r	Exibe o diretorio em ordem de tras para frente.
◦	(r) (minusculo).
◦	-l	Exibe informacoes dos arquivos contidos no diretorio.
◦	Tipos de informacoes contidas na opcao (-l) do comando (ls)  
◦	(ls -l)
▪	drwxr--r-- 1 syslog utmp 1603 16 de marco de 2016 nome_do_arquivo.
◦	Tipos de arquivos:
▪	Consiste no tipo de arquivos contidos na saida do comando.
▪	Primeira letra mostrada na saida do comando.
•	(d)rwxr--r--.
◦	d	Directory = Um arquivo usado para armazenar outros arquivos.
◦	-	Regular File	= Inclui arquivos legíveis, arquivos de imagens, arquivos     binários e arquivos compactados.
◦	l	Symbolic Link = Aponta para outro arquivo.
◦	s	Socket	= Permite a comunicação entre processos.
◦	p	Pipe = Permite a comunicação entre processos.
◦	b	Block File = Usado para se comunicar com o hardware.
◦	c	Character File = Usado para se comunicar com o hardware.
◦	Permissoes:
▪	Consiste nas permissoes dada ao arquivo pelo dono dele.
▪	Nove caracteres apos o tipo de arquivos.
•	 d(rwxr—r--).
◦	r – Read.
▪	Efeito em arquivos:
Permite que o conteudo do arquivo seja lido ou copiado.
▪	Efeito em diretorios:
Sem permissao de execucao no diretorio, permite uma lista não detalhada de arquivos.
Com permissoes de execucao, o comando ls -l pode fornecer uma lista detalhada.
◦	w – Write.
▪	Efeito em arquivos:
Permite que o conteudo seja modificado ou substituido, permite tambem que arquivos sejam adicionados ou removidos de um diretorio.
▪	Efeito em diretorios:
Para que essa permissao funcione, o diretorio tambem deve ter permissoes de execucao.
◦	x – Execute.
▪	Efeitos em arquivos:
Permite que um arquivo seja executado como um processo, embora os arquivos de script tambem exijam permissoes de leitura.
▪	Efeitos em diretorios:
Permite que o usuario mude para o diretorio se os diretorios pai tambem tiverem permissoes de execucao.
◦	Links fisicos:
▪	Indicam quantos links fisicos apontam para o arquivo.
▪	Os links fisicos sao os numeros apos as permissoes:
•	 drwxr--r--(1).
◦	Proprietario do usuario:
▪	Cada arquivo pertence a uma conta de usuario, a qual permite ao proprietario o direito de definir as permissoes do arquivo.
▪	 A propriedade de usuario e o primeiro nome apos os links fisicos.
•	drwxr--r-- 1 (syslog)
◦	Proprietario do grupo:
▪	Indica qual grupo possui este arquivo, isso e importante porque qualquer membro deste grupo tem um conjunto de permissoes no arquivo.
▪	O priprietario do grupo e o segundo nome apos o proprietario do arquivo.
•	drwxr--r-- 1 syslog (utmp)
◦	Tamanho do arquivo:
▪	Exibe o tamanho do arquivo em bytes.
▪	Para diretórios, esse valor não descreve o tamanho total do diretório, mas quantos bytes são reservados para acompanhar os nomes de arquivos no diretório.
•	 Em outras palavras, ignore esse campo para diretórios.
▪	Às vezes, é preferível apresentar o tamanho do arquivo em um tamanho mais legível por humanos, como megabytes ou gigabytes.
•	Para fazer isso, adicione a opção (-h) ao comando (ls -lh):
◦	Importante:
▪	A opção (-h) deve ser usada com a opção (-l).
▪	O tamanho do arquivo e o numero apos o proprietario do grupo.
•	drwxr--r-- 1 syslog utmp (1603)    
◦	Registro de data e hora:
▪	Indica a hora em que o conteúdo do arquivo foi modificado pela última vez.
▪	Para diretórios, esse registro de data e hora indica a última vez que um arquivo foi adicionado ou excluído do diretório.
▪	O registro de data e hora e a data encontrada apos o tamanho do arquivo.
•	 drwxr--r-- 1 syslog utmp 1603 (16 de marco de 2016)
◦	Nome do arquivo:
▪	Campo final que contem o nome  do arquivo ou diretorio.
▪	O nome do arquivo e o ultimo campo localizado no final.
•	 drwxr--r-- 1 syslog utmp 1603 16 de marco de 2016 (nome).
▪	No caso de links simbólicos , o nome do link é exibido junto com uma seta e o nome do caminho do arquivo original.
•	drwxr--r-- 1 syslog utmp 1603 16 de marco de 2016 (/etc/grub.conf ->../boot/grub/grub.conf).
•	O comando (ls) é normalmente usado para listar arquivos em um diretório:
◦	Como resultado, o uso do comando (echo) pode parecer uma escolha estranha.
•	No entanto, há algo no comando (ls) que causa problemas ao listar arquivos usando padrões glob.
◦	Se o comando (ls) receber um nome de diretório, ele exibirá o conteúdo do diretório.
▪	Os nomes dos arquivos no diretório, não apenas o nome do diretório.
◦	Por exemplo se executar o comando:
▪	(ls /etc/ap*).
•	Quando o comando (ls) vê um nome de arquivo como argumento, ele apenas exibe o nome do arquivo.
•	No entanto, para qualquer diretório, ele exibe o conteúdo do diretório, não apenas o nome do diretório.
▪	Isso se torna ainda mais confuso em uma situação como a seguinte:
•	(ls /etc/x*).
◦	O comando (ls) exibiu apenas os arquivos do diretorio.
▪	Existe uma solução simples para esse problema:
•	Sempre use a opção (-d) com globs, que informa ao comando (ls) para exibir o nome dos diretórios, em vez de seu conteúdo.
◦	(ls /etc/x*).

pwd (print working directory)
Imprime o diretório de trabalho, que é o local atual do usuário no sistema de arquivos.

ps
Usado para listar processos atuais que estao sendo executados no terminal.
•	As saidas incluem as seguintes informacoes:
◦	PID:		Identificador do processo, que e exclusivo para o processo.
▪	Esta informacao e util para controlar o processo pelo seu numero de identificacao.

◦	TTY:		Nome do terminal em que o processo esta sendo executado.
▪	Esta informacao e util para distinguir entre diferentes processos que tem o mesmo nome.

◦	TIME:		Quantidade total de tempo do processador usado no processo.
▪	Normalmente essas informacoes não são usadas por usuarios regulares.

◦	CMD:		Comando que iniciou o processo		
◦	Sua sintaxe e a seguinte:
▪	ps [OPCOES]
◦	Opces utilizadas
▪	Opcoes:	Significados:
•	-e		Lista todos os processos do sistema.
•	-f		Fornece informacoes detalhadas sobre os processos.



tee


SOBRE LINHAS DE COMANDO

Caractere de barra vertical ( | ) pipe
Pode ser usado para enviar a saída de um comando para outro.
•	Normalmente, quando um comando tem saída ou gera um erro, a saída é exibida na tela; no entanto, isso não precisa ser o caso.
◦	Em vez de ser impresso na tela, a saída de um comando se torna entrada para o próximo comando.
◦	O caractere de pipe (|) permite que utilize esses comandos não apenas nos arquivos, mas na saída de outros comandos.
▪	Para visualizar mais facilmente o início da saída, canalize-o para o comando head.
•	Por exemplo:
◦	O exemplo a seguir exibe apenas as dez primeiras linhas:
▪	(ls /etc | head)
▪	A saída completa do comando ls é passada para o comando head pelo shell, em vez de ser impressa na tela.
•	O comando head pega essa saída do comando ls como dados de entrada e a saída do head é impressa na tela.
▪	(ls/etc/ssh | tail -5 | n1)
•	No segundo exemplo, a saída do comando ls é primeiro enviada ao comando tail que captura apenas as últimas cinco linhas da saída.
◦	Em seguida, o comando tail envia essas cinco linhas para o comando n1, que os numera 1- 5.

tr
Este comando pega um conjunto de caracteres e os converte em outro conjunto de caracteres.
•	Por exemplo:
◦	Para capitalizar uma linha de texto:
▪	Use o comando tr da seguinte maneira:
•	(tr 'az' 'A-Z')
▪	o comando tr  não suporta argumentos de nome de arquivo
▪	É possível, no entanto, dizer ao shell para obter STDIN de um arquivo em vez do teclado usando o caractere (<):
•	Por Exemplo:
◦	(tr 'az' 'AZ' <exemplo.txt)  
sort
Este comando pode ser usado para reorganizar as linhas de um arquivo ou inserir em dicionario ou ate em ordem numerica.
•	O comando sort pode reorganizar a saída com base no conteúdo de um ou mais campos.
◦	Os campos são determinados por um delimitador de campo contido em cada linha
◦	Na computação, um delimitador é um caractere que separa uma sequência de texto ou dados; o padrão é espaço em branco, como espaços ou tabulações.
•	O exemplo a seguir cria um arquivo pequeno, usando o comando head para capturar as 5 primeiras linhas do arquivo (/etc/passwd) e enviar a saída para um arquivo chamado mypasswd.
◦	(head -5 /etc/passwd> mypasswd)
•	Agora usando o comando sort no arquivo mypasswd
◦	(sort mypasswd)
▪	Após um exame minucioso da saída no exemplo anterior, o comando sort organizou as linhas do arquivo em ordem alfabética.
•	Três opções são usadas para atingir esse tipo:
◦	Opção	            	Função
◦	    -t(caracter)        		Especifica o delimitador de campo.
◦	    -k(number)        		Especifica o numero do campo.
◦	    -n                 		Executa uma classificacao numerica.
◦	    -r                  		Executa uma classificacao reversa.

wc
Fornece o número de linhas, palavras e bytes (1 byte = 1 caractere em um arquivo de texto) para um arquivo e uma contagem total de linhas se mais de um arquivo for especificado.
•	Por padrão, o comando wc permite que até três estatísticas sejam impressas para cada arquivo fornecido, bem como o total dessas estatísticas se mais de um nome de arquivo for fornecido:
◦	Por exemplo:
▪	(wc /etc/passwd/etc/passwd-)
•	Também é possível visualizar apenas estatísticas específicas.
◦	Opção	            Função
▪	-l		Exibe apenas o numero de linhas
▪	-w		Exibe apenas o numero de palavras
▪	-c                 	Exibe apenas o numero de bytes ou qualquer combinacao dessas opções
▪	Por exemplo
•	Se desejar saber o numero total de arquivos no diretorio /etc, canalize  a saida de ls para o wc e conte apenas o numero de linhas:
◦	(ls /etc/ | wc -l)

cut
O comando cut pode extrair colunas de texto de um arquivo ou entrada padrao.
•	Usado principalmente para trabalhar com arquivos de banco de dados delimitados.
◦	Arquivos delimitados sao arquivos que contem colunas separadas por um delimitador.
◦	Por padrao o comando cut espera que sua entrada seja separada pelo caractere de tabulacao porem a opcao (-d) pode especificar delimitadores alternativos, como dois pontos ou virgula.
▪	Opção	            Função
•	 -d                  	Pode especificar delimitadores especificos como dois pontos ou virgula
•	-f                  	Pode especificar quais campos exibir, como um intervalo hifenizado ou uma lista separada por virgulA
•	-c                  	Extrair colunas de texto com base na posicao do caractere.


COMANDOS DE GERENCIALMENTO DE PACOTES.

dpkg
dpkg --print-architecture

apt
Advanced Packet Tool.
•	Programa front-end da ferramenta (dpkg)
◦	Programa front-end  são programas aos quais os usuarios podem ver e interagir.
•	Opcoes utilizadas.
◦	Opcoes:	Significados:
▪	update:		Atualiza a lista de cache dos pacotes disponiveis para atualizacao.
▪	upgrade	Efetua a atualizacao dos pacotes baixados.
▪	cache search:	Procura palavras chaves nos pacotes.
▪	Install:		Instala pacotes encontrados.
•	O comando apt-get install tambem pode atualizar pacotes, se o pacote estiver instalado e uma versao mais recente estiver disponivel.
▪	remove:	Remove um pacote instalado.
▪	purge:		Limpa e remove todas as informacoes do pacote no sitema
•	Exemplo de comando:
◦	apt purge packet_name

cowsay
Boot robo configuravel
•	Utiliza palavras-chaves ou frase como argumento.
◦	Recomendado colocar o argumento entre aspas simples para impedir que o shell interprete caracteres especiais.


SOBRE ADMINISTRACAO DE USUARIOS.

CREATING USERS AND GROUPS
A maioria dos sistemas Linux é configurada para permitir que um usuário não privilegiado (não raiz) efetue login, além de poder executar efetivamente comandos como usuário raiz, direta ou indiretamente.
•	O comando sudo pode ser configurado para conceder a capacidade de executar comandos administrativos selecionados.
•	Se for necessário que os usuários usem o comando sudo para executar comandos administrativos, o sistema registrará quando os usuários executarem esses comandos.
•	Em algumas distribuições, a criação de uma nova conta de usuário também cria automaticamente uma conta de grupo para o usuário, denominada UPG (Grupo Privado do Usuário).
◦	Nesses sistemas, o grupo e o nome de usuário seriam os mesmos, e o único membro desse novo grupo seria o novo usuário.
•	Para distribuições que não criam um UPG, normalmente os novos usuários recebem o grupo users como seu grupo principal.
•	O administrador pode criar manualmente contas de grupo privadas para o usuário, mas é mais comum criar grupos para vários usuários que precisam colaborar.
•	As contas de usuário podem ser modificadas a qualquer momento para adicioná-las ou removê-las das associações de contas de grupo, mas os usuários devem pertencer a pelo menos um grupo para serem usados como grupo principal.
•	Antes de começar a criar usuários, você deve planejar como usar grupos. Os usuários podem ser criados com associações em grupos que já existem ou usuários existentes podem ser modificados para ter associações em grupos existentes.
•	Se você já planejou quais usuários e grupos deseja, é mais eficiente criar seus grupos primeiro e criar seus usuários com a participação deles.
◦	Caso contrário, se você criar seus usuários primeiro e, em seguida, seus grupos, será necessário executar uma etapa extra para modificar seus usuários e torná-los membros de seus grupos.



GROUPS
O motivo mais comum para criar um grupo é fornecer uma maneira de os usuários compartilharem arquivos.
•	Por exemplo, se várias pessoas que trabalham juntas no mesmo projeto e precisarem colaborar em documentos armazenados em arquivos para o projeto.
•	Nesse cenário, o administrador pode tornar essas pessoas membros de um grupo comum, alterar a propriedade do diretório para o novo grupo e definir permissões no diretório que permite que membros do grupo acessem os arquivos.
•	Após criar ou modificar um grupo, você pode verificar as alterações visualizando as informações de configuração do grupo no arquivo /etc/group com o comando grep.
◦	Se estiver trabalhando com serviços de autenticação baseada em rede, o comando getent poderá mostrar grupos locais e baseados em rede.
▪	grep pattern filename
▪	getent database record
•	Para uso local, estes comandos mostram o mesmo resultado, neste caso para o grupo root:
◦	root@localhost:~# grep root /etc/group
◦	root:x:0:
◦	root@localhost:~# getent group root
◦	root:x:0:

CREATING A GROUP
O  comando groupadd pode ser executado pelo usuário root para criar um novo grupo.
•	O comando requer que apenas o nome do grupo seja criado.
◦	A opção -g pode ser usada para especificar um ID de grupo para o novo grupo:
▪	root@localhost:~# groupadd -g 1005 research
▪	root@localhost:~# grep research /etc/group
▪	research:x:1005:
◦	Se a opção -g não for fornecida, o comando groupadd fornecerá automaticamente um GID para o novo grupo.
◦	Para fazer isso, o comando groupadd examina o arquivo /etc/group e usa um número com um valor maior que o número GID mais alto atual.
◦	A execução dos seguintes comandos ilustra isso:
▪	root@localhost:~# groupadd development
▪	root@localhost:~# grep development /etc/group\
▪	development:x:1006:

CONSIDERAÇOES SOBRE CRIAÇÃO DE GRUPO
Em algumas distribuições Linux, particularmente aquelas baseadas no Red Hat, quando um ID do usuário (UID) é criado, um grupo privado de usuários (UPG) também é criado com esse usuário como seu único membro.
•	Nessas distribuições, o UID e o ID do UPG devem corresponder (seja o mesmo número).
•	Portanto, você deve evitar criar GIDs nos mesmos intervalos numéricos em que espera criar UIDs, para evitar um conflito entre um GID criado e um número UPG criado para corresponder a um UID.
•	GIDs sob 500 (RedHat) ou 1000 (Debian) são reservados para uso do sistema.
•	Pode haver momentos em que você deseja atribuir um valor GID mais baixo.
•	Para fazer isso, use a opção -r que atribui ao novo grupo um GID menor que o GID padrão mais baixo:
◦	root@localhost:~# groupadd -r sales
◦	root@localhost:~# getent group sales
◦	sales:x:999:



CONSIDERAÇOES SOBRE NOMEAÇÃO DE GRUPOS
Seguir estas diretrizes para nomes de grupos pode ajudar a selecionar um nome de grupo que seja portátil (funcione corretamente com outros sistemas ou serviços):
•	O primeiro caractere do nome deve ser um sublinhado _caráter ou um alfabético minúsculo a- z personagem.
•	São permitidos até 32 caracteres na maioria das distribuições Linux, mas o uso de mais de 16 pode ser problemático, pois algumas distribuições podem não aceitar mais de 16.
•	Após o primeiro caractere, os caracteres restantes podem ser alfanuméricos, um traço - ou um sublinhado _.
•	O último caractere não deve ser um hífen -.
•	Infelizmente, essas diretrizes nem sempre são aplicadas.
•	O problema não é que o comando groupadd não necessariamente falhe, mas que outros comandos ou serviços do sistema podem não funcionar corretamente.

MODIFICANDO UM GRUPO
O comando groupmod pode ser usado para alterar o nome de um grupo com a opção -n ou alterar o GID do grupo com a opção -g.
•	Alterar o nome do grupo pode confundir os usuários que estavam familiarizados com o nome antigo e não foram informados sobre o novo nome.
•	No entanto, alterar o nome do grupo não causará problemas no acesso a arquivos, pois os arquivos pertencem a GIDs, não a nomes de grupos.
•	Por exemplo:
◦	root@localhost:~# ls -l index.html
◦	-rw-r-----. 1 root sales 0 Aug  1 13:21 index.html
◦	root@localhost:~# groupmod -n clerks sales
◦	root@localhost:~# ls -l index.html
◦	-rw-r-----. 1 root clerks 0 Aug  1 13:21 index.html
•	Após o comando anterior groupmod , arquivo o index.html possui um nome de proprietário de grupo diferente.
•	No entanto, todos os usuários que estavam no grupo sales agora estão no grupo clerks, portanto todos eles ainda podem acessar o arquivo index.html. Novamente, isso ocorre porque o sistema define o grupo pelo GID, não pelo nome do grupo.
•	Por outro lado, se você alterar o GID de um grupo, todos os arquivos associados a esse grupo não serão mais associados a esse grupo.
•	De fato, todos os arquivos associados a esse grupo não serão mais associados a nenhum nome de grupo.
•	Em vez disso, esses arquivos pertencerão apenas a um GID, conforme mostrado abaixo:
◦	root@localhost:~# groupmod -g 10003 clerks
◦	root@localhost:~# ls -l index.html
◦	-rw-r-----. 1 root 491 13370 Aug  1 13:21 index.html
Considere isto
Esses arquivos sem nome de grupo são chamados de arquivos órfãos .
Para procurar todos os arquivos pertencentes a apenas um GID (não associado a um nome de grupo), use a opção -nogroup do  comando find:
root@localhost:~# find / -nogroup
/root/index.html



APAGANDO UM GRUPO
Se você decidir excluir um grupo com o comando groupdel, esteja ciente de que todos os arquivos pertencentes a esse grupo ficarão órfãos.
•	Somente grupos suplementares podem ser excluídos; portanto, se qualquer grupo que for o grupo principal de qualquer usuário, ele não poderá ser excluído.
•	O administrador pode modificar qual grupo é o grupo principal de um usuário, para que um grupo que estava sendo usado como grupo principal possa ser transformado em um grupo suplementar e, em seguida, possa ser excluído.
•	Enquanto o grupo a ser excluído não for o grupo principal de um usuário, a exclusão do grupo será realizada usando o comando groupdel junto com o nome do grupo:
◦	root@localhost:~# groupdel clerks

USUARIOS
As informações da conta do usuário são armazenadas no arquivo /etc/passwd e as informações de autenticação do usuário (dados da senha) são armazenadas no arquivo /etc/shadow.
•	A criação de um novo usuário pode ser realizada adicionando manualmente uma nova linha a cada um desses arquivos, mas essa geralmente não é a técnica recomendada.
•	Antes de começar a criar usuários para o seu sistema, você deve verificar ou estabelecer valores práticos que são usados por padrão com o comando useradd.
•	Essas configurações podem ser encontradas nos arquivos de configuração usados pelo comando useradd.
•	Garantir que os valores nesses arquivos de configuração sejam razoáveis antes da adição de usuários pode ajudar a economizar tempo e problemas para corrigir as configurações da conta de usuário após a adição dos usuários.
◦	ARQUIVOS DE CONFIGURAÇÃO DE USUARIO
▪	A opção  -D para o comando useradd permite visualizar ou alterar alguns dos valores padrão usados pelo comando useradd.
▪	Os valores mostrados por useradd -D também podem ser visualizados ou atualizados manipulando o arquivo /etc/default/useradd:
•	root@localhost:~# useradd -D
•	GROUP=100
•	HOME=/home
•	INACTIVE=-1
•	EXPIRE=
•	SHELL=/bin/bash
•	SKEL=/etc/skel
•	CREATE_MAIL_SPOOL=yes
▪	A seguir, descreve cada um desses valores:
•	Grupo
◦	GROUP=100
▪	Nas distribuições que não usam UPG, este é o grupo principal padrão para um novo usuário, se um não for especificado com o comando useradd.
▪	Este é geralmente o grupo users com um GID de 100.
▪	Essa configuração afeta o campo de ID do grupo principal do arquivo /etc/passwd destacado abaixo:
•	bob:x:600:600:bob:/home/bob:/bin/bash
▪	A opção -g para o comando useradd permite que você use um grupo principal diferente do padrão ao criar uma nova conta de usuário.
•	Home
◦	HOME=/home
▪	O diretório /home é o diretório base padrão no qual o novo diretório inicial do usuário é criado.
▪	Isso significa que um usuário com um nome de conta bob teria um diretório inicial de /home/bob.
▪	Essa configuração afeta o campo do diretório inicial do arquivo /etc/passwd destacado abaixo:
•	bob:x:600:600:bob:/home/bob:/bin/bash
▪	A opção -b para o comando useradd permite que você use um grupo de diretórios base diferente do padrão ao criar uma nova conta de usuário.
•	Inativo
◦	INACTIVE=-1
▪	Este valor representa o número de dias após a senha expirar que a conta está desabilitada.
▪	Um valor -1 significa que esse recurso não está ativado por padrão e nenhum valor "inativo" é fornecido para novas contas por padrão.
▪	Essa configuração afeta o campo inativo do arquivo /etc/shadow destacado abaixo:
•	bob:pw:15020:5:30:7:60:15050:
▪	A opção -f para o comando useradd permite que você use um valor INACTIVE diferente do padrão ao criar uma nova conta de usuário.
•	Expire
◦	EXPIRE=
▪	Por padrão, não há valor definido para a data de validade.
▪	Normalmente, uma data de validade é definida em uma conta individual, nem todas as contas por padrão.
▪	Por exemplo, se você tivesse um contratado que foi contratado para trabalhar até o final do dia em 1º de novembro de 2019, poderá garantir que eles não consigam efetuar logon após essa data usando o  campo EXPIRE
▪	Essa configuração afeta o campo de validade do arquivo /etc/shadow destacado abaixo:
•	bob:pw:15020:5:30:7:60:15050:
▪	A opção -e para o comando useradd permite que você use um  valor EXPIRE diferente do padrão ao criar uma nova conta de usuário.
•	Shell
◦	SHELL=/bin/bash
▪	A configuração SHELL indica o shell padrão para um usuário quando ele efetua login no sistema.
▪	Essa configuração afeta o campo de shell do arquivo /etc/passwd destacado abaixo:
•	bob: x: 600: 600: bob: / casa / bob: / bin / bash
▪	A opção -s para o comando useradd permite que você use um shell de login diferente do padrão ao criar uma nova conta de usuário.
•	Diretorio de esqueleto:
◦	SKEL=/etc/skel
▪	O valor SKEL determina qual diretório do esqueleto tem seu conteúdo copiado no diretório inicial do novo usuário.
▪	O conteúdo desse diretório é copiado para o diretório inicial do novo usuário e o novo usuário recebe a propriedade dos novos arquivos.
▪	Essa configuração fornece aos administradores uma maneira fácil de preencher uma nova conta de usuário com os principais arquivos de configuração.
◦	A opção -k para o comando useradd permite que você use um diretório SKEL diferente do padrão ao criar uma nova conta de usuário.
•	Criar spool de e-mail:
◦	CREATE_MAIL_SPOOL=yes
▪	Um spool de email é um arquivo em que o email recebido é colocado.
▪	Atualmente, o valor para a criação de um spool de correio é yes, o que significa que os usuários por padrão estão configurados com a capacidade de receber e armazenar correio local.
▪	Se você não planeja usar o correio local, esse valor pode ser alterado para no.
▪	Para modificar um dos valores useradd padrão, o arquivo /etc/default/useradd pode ser editado com um editor de texto.
▪	Outra técnica (mais segura) é usar o comando useradd -D
▪	Por exemplo, se você deseja permitir que os usuários tenham senhas expiradas com as quais eles ainda possam efetuar login por até trinta dias, execute:
•	root@localhost:~# useradd -D -f 30
•	root@localhost:~# useradd -D
•	GROUP=100
•	HOME=/home
•	INACTIVE=30
•	EXPIRE=
•	SHELL=/bin/bash
•	SKEL=/etc/skel
•	CREATE_MAIL_SPOOL=yes
ARQUIVOS DE CONFIGURAÇÃO DE USUARIO
O arquivo /etc/login.defs também contém valores que são aplicados por padrão aos novos usuários criados com o comando useradd.
•	Diferentemente do arquivo /etc/default/useradd, o arquivo /etc/login.defs geralmente é editado diretamente pelo administrador para alterar seus valores.
•	Esse arquivo contém muitos comentários e linhas em branco; portanto, para exibir apenas as linhas que não são comentários ou linhas em branco (as configurações reais), você pode usar o seguinte comando grep:
◦	root@localhost:~#  grep -Ev '^#|^$' /etc/login.defs
◦	MAIL_DIR        /var/mail/spool
◦	PASS_MAX_DAYS   99999
◦	PASS_MIN_DAYS   0
◦	PASS_MIN_LEN    5
◦	PASS_WARN_AGE   7
◦	UID_MIN                   500
◦	UID_MAX                 60000
◦	GID_MIN                   500
◦	GID_MAX                 60000
◦	CREATE_HOME     yes
◦	UMASK           077
◦	USERGROUPS_ENAB yes
◦	ENCRYPT_METHOD SHA512
◦	MD5_CRYPT_ENAB no
•	O exemplo acima representa um arquivo /etc/login.defs de distribuição típico do CentOS 6 com seus valores.
•	A seguir, descreve cada um desses valores:
◦	Diretório de Correio
▪	MAIL_DIR                /var/mail/spool
•	O diretório no qual o arquivo de spool de correio do usuário é criado.
◦	Dias máximos da senha
▪	PASS_MAX_DAYS   99999
•	Essa configuração determina o número máximo de dias em que um usuário pode continuar usando a mesma senha.
•	Como o padrão é 99999 dias (mais de 200 anos), efetivamente significa que os usuários nunca precisam alterar sua senha.
•	As organizações com políticas eficazes para manter senhas seguras geralmente alteram esse valor para 60 ou 30 dias.
•	Essa configuração afeta a configuração padrão do arquivo /etc/shadow destacado abaixo:
◦	bob:pw:15020:5:30:7:60:15050:
◦	Dias mínimos da senha
▪	PASS_MIN_DAYS 0
•	Com esse conjunto com um valor padrão igual a zero, o menor tempo necessário para que um usuário mantenha uma senha é zero dias, o que significa que ele pode alterar imediatamente uma senha que acabou de definir.
•	Se o valor  PASS_MIN_DAYS foi definido como três dias, depois de definir uma nova senha, o usuário precisaria aguardar três dias para poder alterá-lo novamente.
•	Essa configuração afeta a configuração padrão do arquivo /etc/shadow destacado abaixo:
◦	bob:pw:15020:3:30:7:60:15050:
◦	Comprimento mínimo da senha
▪	PASS_MIN_LEN 5
•	Isso indica o número mínimo de caracteres que uma senha deve conter.
•	Aviso de senha
◦	PASS_WARN_AGE 7
•	Este é o padrão para o campo de aviso.
•	À medida que um usuário se aproxima do número máximo de dias em que pode usar sua senha, o sistema verifica se é hora de começar a alertar o usuário sobre a alteração de sua senha no login.
•	Essa configuração afeta a configuração padrão do arquivo /etc/shadow destacado abaixo:
◦	bob: pw: 15020:3:30:7:60: 15050:
◦	Mínimo de UID
▪	UID_MIN 500
•	O UID_MIN determina o primeiro UID que é atribuído a um usuário comum.
•	Qualquer UID menor que esse valor seria para uma conta do sistema ou a conta raiz.
◦	UID Máximo
▪	UID_MAX 60000
•	Um UID tecnicamente pode ter um valor superior a quatro bilhões.
•	Para obter compatibilidade máxima, é recomendável deixá-lo no valor padrão de 60000.
◦	Mínimo de GID
▪	GID_MIN 500
•	O GID_MIN determina o primeiro GID que é atribuído a um grupo comum.
•	Qualquer grupo com um GID menor que esse valor seria um grupo do sistema ou o grupo raiz.
◦	GID Máximo
▪	GID_MAX 60000
•	Um GID, como um UID, pode ter um valor superior a quatro bilhões.
•	Qualquer que seja o valor que você use para o seu UID_MAX, deve ser usado para GID_MAX apoiar o UPG.
◦	Diretório Inicial
▪	CREATE_HOME sim
•	O valor disso determina se um novo diretório é criado ou não para o usuário quando sua conta é criada.
◦	Umask
▪	UMASK 077
•	UMASK funciona no momento em que o diretório inicial do usuário está sendo criado; determina quais permissões padrão são colocadas nesse diretório.
•	Usar o valor padrão de 077para UMASK significa que apenas o proprietário do usuário tem algum tipo de permissão para acessar seu diretório.
◦	UPG
▪	USERGROUPS_ENAB sim
•	Nas distribuições que apresentam um grupo privado para cada usuário, como mostra o exemplo do CentOS, o valor USERGROUPS_ENAB terá yes. Se UPG não for usado na distribuição, isso terá um valor de no.
◦	Criptografia
▪	ENCRYPT_METHOD SHA512
•	O método de criptografia usado para criptografar as senhas dos usuários no arquivo /etc/shadow.
◦	A configuração ENCRYPT_METHOD substitui a configuração MD5_CRYPT_ENAB.
◦	Criptografia (descontinuada)
▪	MD5_CRYPT_ENAB no
•	Essa configuração descontinuada originalmente permitiu ao administrador especificar o uso da criptografia MD5 de senhas em vez da criptografia DES original.
•	Ele foi substituído pela configuração ENCRYPT_METHOD.
CONSIDERAÇÕES SOBRE A CONTA
Criar uma conta de usuário para uso com um sistema Linux pode exigir que você colete várias informações.
•	Embora tudo o que seja necessário seja o nome da conta, você também pode planejar o UID, o grupo principal, os grupos suplementares, o diretório inicial, o diretório do esqueleto e o shell a ser usado.
•	Ao planejar esses valores, considere o seguinte:
◦	O único argumento necessário para o comando useradd é o nome que você deseja que a conta tenha.
◦	O nome de usuário deve seguir as mesmas diretrizes dos nomes de grupos.
◦	Seguir estas diretrizes pode ajudá-lo a selecionar um nome de usuário portátil:
▪	O primeiro caractere do nome deve ser um _caractere sublinhado ou um caractere alfabético  a-z em minúsculas .
▪	São permitidos até 32 caracteres na maioria das distribuições Linux, mas o uso de mais de 16 pode ser problemático, pois algumas distribuições podem não aceitar mais de 16.
▪	Após o primeiro caractere, os caracteres restantes podem ser alfanuméricos, um traço - ou um sublinhado _ .
▪	O último caractere não deve ser um caractere  hífen -.
◦	Se o usuário precisar acessar vários sistemas, geralmente é recomendável que o nome da conta seja o mesmo nesses sistemas.
◦	O nome da conta deve ser exclusivo para cada usuário.
▪	root@localhost:~# useradd jane
•	Identificador do usuário (UID)
◦	Depois de criar um usuário com um UID específico, o sistema geralmente incrementa o UID em um para o próximo usuário que você criar.
◦	Se conectado a uma rede com outros sistemas, convém garantir que esse UID seja o mesmo em todos os sistemas para ajudar a fornecer acesso consistente.
◦	Adicionar a opção -u ao comando useradd permite especificar o número do UID.
◦	Os UIDs geralmente podem variar de zero a mais de quatro bilhões, mas para maior compatibilidade com sistemas mais antigos, o valor UID máximo recomendado é de 60.000.
▪	root @ localhost : ~ # useradd -u 1000 jane
◦	O usuário root possui um UID de 0, o que permite que essa conta tenha privilégios especiais.
◦	Qualquer conta com um UID de 0 poderia efetivamente atuar como administrador.
◦	As contas do sistema geralmente são usadas para executar serviços em segundo plano chamados daemons .
◦	Por não ter os serviços executados como usuário root, a quantidade de dano que pode ser causado com uma conta de serviço comprometida é limitada.
◦	As contas do sistema usadas pelos serviços geralmente usam UIDs que estão no intervalo reservado.
▪	Uma conta do sistema que é uma exceção a essa regra é o usuário nfsnobody, que possui um UID de 65534.
◦	O intervalo reservado usado para contas de serviço se expandiu ao longo do tempo.
◦	Inicialmente, era para UIDs entre 1 e 99.
◦	Em seguida, expandiu-se para entre 1 e 499.
◦	A tendência atual entre distribuições é que as contas do sistema sejam qualquer conta que tenha um UID entre 1 e 999, mas o intervalo de 1-499 é também ainda é comumente usado.
◦	Ao configurar um novo sistema, é uma boa prática iniciar UIDs inferiores a 1000, garantindo que haja UIDs suficientes disponíveis para muitos serviços do sistema e oferecendo a capacidade de criar muitos GIDs no intervalo reservado.
GRUPO PRIMÁRIO
Nas distribuições que apresentam UPG, esse grupo é criado automaticamente com um GID e um nome de grupo que correspondem ao UID e ao nome de usuário da conta de usuário recém-criada.
•	Nas distribuições que não usam UPG, o grupo principal normalmente assume como padrão o grupo users  com um GID de 100.
•	Para especificar um grupo principal com o comando useradd, use a opção -g com o nome ou o GID do grupo.
•	Por exemplo, para especificar users como o grupo principal:
◦	root@localhost:~# useradd -g users jane
GRUPO SUPLEMENTARES
Para tornar o usuário membro de um ou mais grupos suplementares, a opção -G pode ser usada para especificar uma lista separada por vírgula de nomes ou números de grupos.
•	Por exemplo, para especificar sales e research como grupos suplementares:
◦	root@localhost:~# useradd -G sales, research jane
DIRETORIO INICIAL
Por padrão, a maioria das distribuições cria o diretório inicial do usuário com o mesmo nome da conta do usuário, independentemente do diretório base especificado na configuração HOME do arquivo /etc/default/useradd, que normalmente especifica o diretório /home.
•	Por exemplo, se criar uma conta de usuário nomeada jane, o novo diretório inicial do usuário seria /home/jane.
◦	root@localhost:~# useradd jane
◦	root@localhost:~# grep'/home/jane'/etc/passwd
◦	jane:x:1008:1010::/home/jane:/bin/sh
•	Existem várias opções para o comando useradd que podem afetar a criação do diretório inicial do usuário:
•	Se CREATE_HOME estiver definido como no ou se essa configuração não estiver presente, o diretório não será criado automaticamente.
•	Caso contrário, a opção -M é usada para especificar no comando useradd que ele não deve criar o diretório inicial, mesmo que CREATE_HOME esteja definido como yes.
•	Se a configuração CREATE_HOME no arquivo /etc/login.defs estiver definida como yes, o diretório inicial será criado automaticamente.
•	Caso contrário, a opção -m pode ser usada para criar o diretório inicial.
◦	root @ localhost : ~ # useradd -m jane
◦	root @ localhost : ~ # ls -ld / home / jane                                             
◦	drwxr-xr-x 2 jane jane 4096 dez 18 19:14 / home / jane
•	A opção -b permite especificar um diretório base diferente no qual o diretório inicial do usuário é criado.
•	Por exemplo, o seguinte cria a conta de usuário jane com um /test/jane criado como o diretório home do usuário:
◦	root @ localhost : ~ # useradd -mb / test jane
◦	raiz @ localhost : ~ # ls -ld / test / Jane
◦	drwxr-xr-x 2 jane jane 4096 dez 18 19:16 / test / jane
•	A opção -d permite especificar um diretório existente ou um novo diretório inicial a ser criado para o usuário.
•	Esse deve ser um caminho completo para o diretório inicial do usuário.
•	Por exemplo, o seguinte cria a conta de usuário jane com um /test/jane criado como o diretório home do usuário:
◦	root @ localhost : ~ # useradd -md / test / jane jane
◦	root @ localhost : ~ # ls -ld / test / jane
◦	drwxr-xr-x 2 jane jane 4096 dez 18 19:19 / test / jane
•	A opção -k para especificar um diretório esqueleto diferente.
•	Ao usar a opção -k, a opção -m é necessária.
DIRETORIO DE ESQUELETOS
Por padrão, o conteúdo do diretório /etc/skel é copiado no diretório inicial do novo usuário.
•	Os arquivos resultantes também são de propriedade do novo usuário.
•	Usando a opção -k com o comando useradd, o conteúdo de um diretório diferente pode ser usado para preencher o diretório inicial de um novo usuário.
•	Ao especificar o diretório esqueleto com a opção -k, a opção -m deve ser usada ou o comando useradd falhará com um erro.
•	O exemplo a seguir usa /home/sysadmin como diretório esqueleto:
◦	root @ localhost : ~ # useradd -mk / home / sysadmin jane
◦	root @ localhost : ~ # ls / home / jane
•	Documentos para desktop Downloads Músicas Fotos Modelos públicos Videos
SHELL
Embora o shell padrão esteja especificado no arquivo /etc/default/useradd, ele também pode ser substituído pelo comando useradd usando a opção -s no momento da criação da conta:
•	root @ localhost : ~ # useradd -s / bin / bash jane
•	É comum especificar o shell /sbin/nologin para que as contas sejam usadas como contas do sistema.

COMMENT
O campo de comentário, originalmente chamado de campo General Electric Comprehensive Operating System (GECOS), geralmente é usado para armazenar o nome completo do usuário.
•	Muitos programas gráficos de login exibem o valor desse campo em vez do nome da conta.
•	A opção -c do comando useradd permite que o valor desse campo seja especificado.
◦	root @ localhost : ~ # useradd -c 'Jane Doe' jane

CRIANDO UM USUARIO
Depois de verificar quais valores padrão usar e reunir as informações sobre o usuário, você estará pronto para criar uma conta de usuário.
•	Um exemplo de comando useradd usando algumas opções é semelhante ao seguinte:
◦	root @ localhost : ~ # useradd -u 1009 -g usuários -G de vendas, pesquisa -m -c 'Jane Doe' jane
•	Este exemplo do comando useradd cria um usuário com um UID de 1009, um grupo principal de usuários, associações suplementares nos grupos sales e research, um comentário "Jane Doe"e um nome de conta jane.
•	Depois de executar o comando anterior, as informações sobre a conta do usuário jane  são automaticamente adicionadas aos arquivos /etc/passwd e /etc/shadow, enquanto as informações sobre o acesso suplementar ao grupo são automaticamente adicionadas aos arquivos /etc/group e /etc/gshadow:
◦	root @ localhost : ~ # grep jane / etc / passwd
◦	jane : x: 1009: 100: Jane Doe: / home / jane : / bin / sh
◦	root @ localhost : ~ # grep jane / etc / shadow
◦	jane :!: 17883: 0: 99999: 7: 30 ::
◦	root @ localhost : ~ # grep jane / etc / group
◦	research: x: 1005: jane
◦	sales: x: 999: jane
◦	root @ localhost : ~ # grep jane / etc / gshadow
◦	research :! :: Jane
◦	Sales :! :: Jane
•	Observe que a conta ainda não tem uma senha válida!
•	Além disso, se o CREATE_MAIL_SPOOL estiver definido como yes, o arquivo de spool de correio /var/spool/mail/jane será criado:
◦	root @ localhost : ~ # ls / var / spool / mail
◦	jane raiz rpc sysadmin
•	Por fim, como a opção -m é usada, o diretório /home/jane é criado com permissões que permitem apenas o jane acesso do usuário e o conteúdo do diretório /etc/skel é copiado para o diretório:
◦	root @ localhost : ~ # ls / home
◦	jane sysadmin
SENHAS
É fácil criar uma senha incorreta! Se você usar alguma informação em sua senha relacionada a você, essas informações também poderão ser conhecidas ou descobertas por outras pessoas, resultando em sua senha ser facilmente comprometida.
•	Sua senha nunca deve conter informações sobre você ou qualquer pessoa que você conheça, como seu primeiro nome, nome do meio, sobrenome, data de nascimento, telefone, nomes de animais de estimação, carteira de motorista ou número de segurança social.
•	Existem vários fatores a serem considerados ao tentar escolher uma senha para uma conta:
◦	Comprimento :
▪	o arquivo /etc/login.defs permite que o administrador especifique o tamanho mínimo da senha.
▪	Enquanto alguns acreditam que quanto maior a senha, melhor, isso não está realmente correto.
▪	O problema com senhas muito longas é que elas não são facilmente lembradas e, como resultado, geralmente são anotadas em um local onde podem ser facilmente encontradas e comprometidas.
◦	Composição :
▪	Uma boa senha deve ser composta por uma combinação de caracteres alfabéticos, numéricos e simbólicos.
◦	Vida útil :
▪	A quantidade máxima de tempo que uma senha pode ser usada deve ser limitada por vários motivos:
•	Se uma conta for comprometida e o tempo de validade da senha for limitado, o invasor perderá o acesso quando a senha se tornar inválida.
•	Se uma conta não estiver sendo usada, ela poderá ser desativada automaticamente quando a senha não for mais válida.
•	Se os invasores estiverem tentando um ataque de "força bruta" tentando todas as senhas possíveis, a senha poderá ser alterada antes que o ataque seja bem-sucedido.
•	No entanto, exigir que um usuário altere sua senha com muita frequência pode causar problemas de segurança, incluindo:
◦	A qualidade da senha escolhida pelo usuário pode sofrer.
◦	O usuário pode começar a escrever sua senha no papel, aumentando a possibilidade de a senha ser descoberta.
◦	As contas de usuário raramente usadas podem expirar e requerem atenção administrativa para redefinir.

DEFENINDO UMA SENHA DE USUARIO
Existem várias maneiras de alterar uma senha de usuário.
•	O usuário pode executar o comando passwd, o administrador pode executar o comando passwd fornecendo o nome de usuário como argumento ou também estão disponíveis ferramentas gráficas.
•	O administrador pode usar o comando passwd para definir a senha inicial ou alterar a senha da conta.
•	Por exemplo, se o administrador criou a conta jane, a execução passwd jane fornece ao administrador um prompt para definir a senha da conta jane.
•	Se concluído com êxito, o arquivo /etc/shadow será atualizado com a nova senha do usuário.
•	Embora os usuários regulares precisem seguir muitas regras de senha, o usuário root precisa seguir apenas uma regra:
◦	A senha não pode ser deixada em branco.
◦	Quando o usuário root viola todas as outras regras de senha que normalmente se aplicam a usuários regulares, isso resulta em um aviso sendo impresso na tela e a regra não sendo aplicada:
▪	root @ localhost : ~ # passwd Jane
▪	Digite a nova senha UNIX:
▪	SENHA RUIM: É UMA MANEIRA abreviar
▪	SENHA RUIM: é muito simples
▪	Digite a nova senha UNIX:
•	Supondo que o administrador tenha definido uma senha para uma conta de usuário, o usuário poderá fazer login com esse nome de conta e senha.
•	Depois que o usuário abre um terminal, ele pode executar o comando passwd sem argumentos para alterar sua própria senha.
•	Eles são solicitados a senha atual e, em seguida, solicitados a inserir a nova senha duas vezes.
•	Como usuário comum, pode ser difícil definir uma senha válida porque todas as regras para a senha devem ser seguidas.
•	Normalmente, o usuário tem três tentativas para fornecer uma senha válida antes que o comando passwd saia com um erro.
•	Usando os privilégios do usuário root, as senhas criptografadas e outras informações relacionadas à senha podem ser visualizadas visualizando o arquivo /etc/shadow.
•	Lembre-se de que usuários comuns não podem ver o conteúdo deste arquivo.
GERENCIANDO O ENVELHECIMENTO DA SENHA
O comando chage fornece muitas opções para gerenciar as informações de duração da senha encontradas no arquivo /etc/shadow.
•	Um bom exemplo do comando chage seria alterar o número máximo de dias em que a senha de um indivíduo é válida para 60 dias:
◦	root @ localhost : ~ # chage -M 60 jane
◦	root @ localhost : ~ # grep jane / etc / shadow | cut -d: -f1,5
◦	Jane: 60

MODIFICANDO UM USUARIO
Antes de fazer alterações em uma conta de usuário, entenda que alguns comandos não modificarão com êxito uma conta de usuário se o usuário estiver conectado no momento (como alterar o nome de login do usuário).
•	Outras alterações que você pode fazer não serão efetivas se o usuário estiver conectado, mas entrarão em vigor assim que o usuário efetuar logout e depois efetuar login novamente.
•	Por exemplo, ao modificar associações de grupos, as novas associações ficarão indisponíveis para o usuário até a próxima vez que o usuário efetuar login.
•	Em ambos os casos, é útil saber como usar os comandos who, w e last , para que possa estar ciente de quem está logado no sistema, pois isso pode afetar as mudanças que você quer fazer para uma conta de usuário.
•	Tanto os comandos who e ou w mostra que está conectado ao sistema.
◦	 O comando w é o mais detalhado dos dois, pois mostra o tempo de atividade e a carga do sistema, bem como o processo que cada usuário está executando.
◦	O comando last pode ser usado para determinar as sessões de login atuais e anteriores, bem como sua data e hora específicas.
•	Ao fornecer um nome de usuário ou um nome tty(terminal) como argumento, o comando mostra apenas os registros que correspondem a esse nome.
•	O comando usermod oferece muitas opções para modificar uma conta de usuário existente.
◦	Muitas dessas opções também estão disponíveis com o comando useradd no momento em que a conta é criada.
◦	Várias dessas opções são dignas de discussão por causa de como elas impactam o gerenciamento de usuários.
◦	Pode ser muito problemático alterar o UID do usuário com a opção -u, pois todos os arquivos pertencentes ao usuário ficam órfãos.
◦	Por outro lado, especificar um novo nome de login para o usuário -l não torna os arquivos órfãos.
•	A exclusão de um usuário com o comando userdel pode tornar órfão ou remover os arquivos do usuário no sistema.
•	Em vez de excluir a conta, outra opção é bloquear a conta com a opção -L para o comando usermod.
•	O bloqueio de uma conta impede que a conta seja usada, mas a propriedade dos arquivos permanece.
•	Há algumas coisas importantes a saber sobre como gerenciar os grupos suplementares.
•	Se você usar a opção -G sem a opção -a, deverá listar todos os grupos aos quais o usuário pertenceria.
•	Usar a opção -G sozinha pode levar à remoção acidental de um usuário de todos os grupos suplementares anteriores aos quais o usuário pertencia.
◦	Se você usar a opção -a -G, precisará listar apenas os novos grupos aos quais o usuário pertenceria.
•	Por exemplo, se o usuário pertencer jane atualmente aos grupos sales e research, para adicionar sua conta ao grupo development, execute o seguinte comando:
◦	root@localhost:~# usermod -aG desenvolvimento jane

APAGANDO UM USUARIO
O comando userdel é usado para excluir usuários.
•	Ao excluir uma conta de usuário, você também precisa decidir se deseja excluir o diretório inicial do usuário.
•	Os arquivos do usuário podem ser importantes para a organização e pode haver requisitos legais para manter os dados por um certo período de tempo, portanto, tome cuidado para não tomar essa decisão de ânimo leve.
•	Além disso, a menos que você tenha feito cópias de segurança dos dados, depois de executar o comando para excluir o usuário e seus arquivos, não há como reverter a ação.
•	Para excluir o usuário jane sem excluir o diretório inicial do usuário /home/jane, execute:
◦	root @ localhost : ~ # userdel jane
◦	Cuidado ao excluir um usuário sem excluir o diretório inicial significa que os arquivos do diretório inicial ficarão órfãos e esses arquivos pertencerão somente ao seu antigo UID e GID.
•	Para excluir também o usuário, o diretório inicial e o spool de correio, use a opção -r:
◦	root @ localhost : ~ # userdel -r jane

AVISO: O comando acima excluirá apenas os arquivos do usuário no diretório inicial e no spool de correio. Se o usuário possuir outros arquivos fora do diretório inicial, esses arquivos continuarão a existir como arquivos órfãos.

•	Contas de usuário em distribuições Linux baseadas em RedHat, como a distribuição CentOS, começam com o primeiro ID de usuário (UID) em 500, o próximo UID fornecido em 501 e assim por diante.
•	A tendência atual seguida por muitas outras distribuições é fazer com que o primeiro UID seja 1000, o segundo seja 1001 e assim por diante.
•	A partir do RedHat 7, as contas de usuário padrão começam em 1000, uma consideração ao migrar sistemas mais antigos com contas de usuário existentes.
•	Se estiver gerenciando contas para vários sistemas, é desejável ter um servidor de autenticação baseado em rede, onde as contas podem ser criadas uma vez, mas usadas em muitas máquinas.
•	Caso contrário, o gerenciamento de várias contas em várias máquinas pode ser desafiador, pois pode ser difícil garantir que o usuário e todos os grupos a que pertencem tenham os mesmos UIDs e GIDs em todas as máquinas.
•	Outro problema com contas de várias máquinas é que pode ser difícil manter as senhas de cada conta sincronizadas em todas as máquinas.
•	Gerenciar contas para usuários locais ainda é útil para máquinas individuais, mesmo se elas tiverem acesso a um servidor de autenticação baseado em rede.

CONFIGURAÇÕES DE USUÁRIO:
A configuração do usuário começa com a configuração adequada dos grupos nos quais os usuários serão colocados.
•	O valor SKEL fornece aos administradores uma maneira fácil de preencher uma nova conta de usuário com arquivos de configuração de chave.
•	Ele determina qual diretório esqueleto terá seu conteúdo copiado para o diretório inicial do novo usuário.
◦	A opção -k no comando useradd permite que um diretório SKEL diferente do padrão seja usado ao criar uma nova conta de usuário.
◦	Isso é útil porque a maioria dos sistemas possui usuários que precisam de acesso a diferentes recursos, conforme apropriado para suas funções de trabalho.
•	No exemplo abaixo, a opção -D especifica alterações nos valores padrão usados ao criar um novo usuário.
•	A opção -f 30 especifica que os usuários com senhas expiradas ainda podem fazer login por até trinta dias antes que suas contas sejam desativadas.
•	Usar a opção -D por si só exibe os padrões atuais, que foram alterados pelo comando anterior.
◦	root @ localhost : ~ # useradd -D -f 30
◦	root @ localhost : ~ # useradd -D
◦	GROUP = 100
◦	HOME = / home
◦	INACTIVE = 30
◦	EXPIRE =
◦	SHELL = / bin / sh
◦	SKEL = / etc / skel
◦	CREATE_MAIL_SPOOL = no
◦	root @ localhost : ~ #
•	A saída do comando last deve mostrar que o usuário sysadmin já efetuou login antes, mas não o usuário student.
•	Há também um comando lastb que funciona de maneira semelhante ao comando last, exceto que mostra tentativas de login "ruins" ou com falha.
•	Se você não quiser mais que o usuário student tenha acesso ao sistema, o comando usermod -L student pode ser usado para "bloquear" a conta.
•	A conta pode ser desbloqueada com o comando usermod -U student.
•	Uma solução mais permanente para impedir o acesso à conta student seria excluí-la com os comandos userdel student ou userdel -r student.
•	Usar a opção -r com o comando userdel remove o diretório pessoal e o correio do usuário, além de excluir a conta do usuário.

COMANDOS DE ADMINISTRACAO DE USUARIOS E GRUPOS.

su
Permite que você atue temporariamente como um usuario diferente.
•	Por padrao:
◦	Se uma conta de usuario não for especificada, o comando (su) abrira um novo shell como usuario root, que forncesse privilegios administrativos.
▪	O shell e simplesmente um console de entrada de texto que permite digitar comandos.
▪	E recomendavel utilizar a opção de shell de login, pois o shell de loguin configura completamente o novo shell com as configuracoes do no usuario.
•	Esta opção pode ser especificada de tres maneiras:
◦	su -
◦	su -l
◦	su –login
▪	Apos a execucao de quaisquer um dos comandos o shell solicitara uma senha.

“Para evitar a execucao de comandos confidenciais, configuramos o comando Steam Locomotive, para exigir acsso administrativo.
•	Tambem digitados como (sl)”.

sudo
permite que um usuario execute um comando como outro usuario sem criar um novo shell.
•	Em vez disso, para executar um comando com privilegios administrativos, use-o como argumento para o comando (sudo).
◦	Assim como o comando (su), o comando (sudo) assume por padrao que a conta root do usuario deve ser usada para executar comandos.
▪	Para especificar uma conta de usurio diferente, utilize o comando seguido da opção:
•	(sudo -u)
◦	O prompt para senha não aparecera novamente enquanto o usuario continuar executando comandos (sudo) com menos de cinco minutos de intervalo.
◦	O comando (sudo) fornece apenas acesso administrativo para a execucao do comando especificado.
◦	A intensao de executar um comando e clara:
▪	O comando e executado como root se precedir pelo comando (sudo), caso contrario, o comando sera executado como um usuario comum.

useradd

userdel

usermod

newgrp

groupadd

groupmod

groupdel

getent

chmod
Usado para alterar permissoes de um arquivo ou diretorio.
•	Somente o usuario root ou proprietario do arquivo pode alterar as permissoes de um arquivo.
◦	Por que o comando e nomeado de (chmod) em vez de (chperm)?
▪	As permissoes costumam ser chamadas de Modos de acesso, portanto, o comando (chmod) realmente significa Alterar modos de acesso.
◦	Existem duas tecnicas para alterar permissoes com o comando (chmod):
▪	Simbolico:
•	E bom para para alterar um conjunto de permissoes por vez.
•	Sua sintaxe e a seguinte:
◦	chmod [<SET> <ACTION><PERMISSIONS>]... ARQUIVO.
▪	Opcoes sobre SET.
•	Simbolo:	Significado:
◦	u		Usuario: O usuario que possuio o arquivo.
◦	g		Grupo: O grupo que possui o arquivo.
◦	o		Outros: Qualquer pessoa que não seja o proprietario do usuario ou membro do proprietario do grupo.
◦	a		Tudo: Refere-se ao usuario, grupo e outros.
▪	Opcoes sobre ACTION.
•	Simbolo:	Significado:
◦	+		Adicione a permissao, se necessario.
◦	=		Especifique  a permissao exata.
◦	-		Remova a permissao, se necessario.
▪	Opcoes sobre PERMISSIONS.
•	Simbolo:	Significado:
◦	r		Ler
◦	w		Escrever
◦	x		Executar
▪	Exemplo de comando
•	(chmod u +x arquivo.sh)
◦	Uma combinacao de caracteres (./) pode ser usado antes do nome do arquivo para executa-lo.
Isso indica que o comando deve ser executado no diretorio atual.
▪	Octal:
•	O metodo octal ou numerico requer conhecimento do valor octal de cada uma das permissoes e exige que todos os tres conjuntos de permissoes (usuario, grupo, outro), seja especificados sempre.

chown
Usado para alterar a propriedade de arquivos e diretorios.
•	Alterar o proprietario do usuario requer acesso administrativo.
◦	Mesmo para atribuir a propriedade de um de seus próprios arquivos a outro usuario.
▪	No entanto o comando (chown) tambem permite alterar a propriedade do grupo, o que pode ser realizado pela raiz ou pelo proprietario do grupo.
•	Sua sintaxe e a seguinte:
◦	chown [OPTIONS] [PROPRIETARIO]… ARQUIVO.
◦	O primeiro arqumento, [OWNER] especifica qual usuario deve ser o novo proprietario.
◦	O segundo arqumento, [FILE] especifica qual propriedade do arquivo esta sendo alterada.
◦	Somente o proprietario do usuario tem, a permissao de execucao.

chgrp
O comando chgrp pode ser usado para alterar o proprietario do grupo de qualquer arquivo para qualquer grupo.

stat
O comando start exiber informacoes mais detalhadas sobre um arquivo, incluindo o fornecimento da propriedade do grupo por nome do grupo e numero GID

umask
O comando umask é um recurso usado para determinar as permissões padrão definidas quando um arquivo ou diretório é criado.
•	O primeiro valor indica que o umask é fornecido como um número octal.
•	O segundo valor indica quais permissões subtrair das permissões do proprietário do usuário padrão.
•	O terceiro valor indica quais permissões subtrair das permissões do proprietário do grupo padrão.
•	O último valor indica quais permissões subtrair das permissões padrão do outro.

passwd
Usado para atualizar a senha de um usuario.
•	Os usuarios podem alterar apenas suas próprias senhas.
◦	Enquanto o root pode atualizar a senha para qualquer usuario.
•	Sua sintaxe e a seguinte:
◦	passwd [OPCOES] [USUARIO]
•	Opcoes utilizadas
◦	Opcoes:	Significado:
▪	-S		Visualiza informacoes de status sobre a senha
•	Exemplo:
◦	(passwd -S sysadmin).
▪	sysadmin P 16/03/2016 0 99999 7 -1
•	As informacoes de saida são a seguinte:
◦	Nome de usuario:
▪	Indica o nome do usuario
•	sysadmin P 16/03/2016 0 99999 7 -1
◦	Status da senha:
▪	p	Indica uma senha utilizavel.
▪	L	Indica uma senha bloqueada.
▪	NP	Indica sem senha.
•	sysadmin P 16/03/2016 0 99999 7 -1
◦	Data da mudanca:
▪	A data  em que a senha foi alterada pela ultima vez.
•	sysadmin P 16/03/2016 0 99999 7 -1
◦	Minimo:
▪	O numero minimo de dias que devem passar antes que a senha atual possa ser alterada pelo usuario.
•	sysadmin P 16/03/2016 0 99999 7 -1
◦	Maximo:
▪	Numero maximo de dias restantes para senha expirar.
•	sysadmin P 16/03/2016 0 99999 7 -1
◦	Advertir:
▪	Numero de dias antes da expiracao da senha que o usuario e avisado.
•	sysadmin P 16/03/2016 0 99999 7 -1
◦	Inativo:
▪	Numero de dias após a expiracao da senha que a conta do usuario permanece ativa.
•	sysadmin P 16/03/2016 0 99999 7 -1

shutdown
Organiza para que o sistema seja desativado de maneira segura.
•	Todos os usuarios conectados são notificados de que o sistema esta inoperando e, nos ultimos 5 minutos que antecedem o desligamento, novos logins são impedidos.
◦	Sua sintaxe e a seguinte:
▪	shutdown [OPCOES] HORA [MENSAGEM]

date
Usado para informar informacoes de data hora e calendario do sistema.

w
Mostra quem esta conectado.

who

last

chage

id




SOBRE CONFIGURACOES BASICAS DE REDE


Terminologia básica de rede

Host
Um host é um computador.
•	Muitas pessoas pensam automaticamente em um computador ou laptop quando ouvem o termo computador.
•	Na realidade, muitos outros dispositivos, como telefones celulares, tocadores de música digital e muitas televisões modernas, também são computadores.
•	Em termos de rede, um host é qualquer dispositivo que se comunica via rede com outro dispositivo.

Network
Uma rede é uma coleção de dois ou mais hosts (computadores) capazes de se comunicar.
•	Essa comunicação pode ser feita através de uma conexão com fio ou sem fio.

Wi-fi
O termo Wi-Fi refere - se a redes sem fio.

Internet
A Internet é um exemplo de rede.
•	Consiste em uma rede acessível ao público que conecta milhões de hosts em todo o mundo.
•	 Muitas pessoas usam a Internet para navegar em páginas da Web e trocar e-mails, mas a Internet possui muitos recursos adicionais além dessas atividades.

Server
Um host que fornece um serviço para outro host ou cliente é chamado de servidor.
•	Por exemplo:
◦	Um servidor da Web armazena, processa e entrega páginas da Web.
◦	Um servidor de email recebe e-mails recebidos e entrega e-mails enviados.

Service
Um recurso fornecido por um host é um serviço.
•	Um exemplo de serviço seria quando um host fornece páginas da web para outro host.

Client
Um cliente é um host que está acessando um servidor.
•	Quando você está trabalhando em um computador navegando na Internet, é considerado um host de cliente.

Router
Também chamado de gateway, um roteador é uma máquina que conecta hosts de uma rede a outra rede.
•	Por exemplo, se você trabalha em um ambiente de escritório, todos os computadores da empresa podem se comunicar por meio da rede local criada pelos administradores.
•	Para acessar a Internet, os computadores precisariam se comunicar com um roteador que seria usado para encaminhar as comunicações de rede para a Internet.
•	Normalmente, quando você se comunica em uma rede grande (como a Internet), vários roteadores são usados antes que sua comunicação chegue ao seu destino final.

Terminologia basica dos recursos de rede

Packet
Um pacote de rede é usado para enviar comunicação de rede entre hosts.
•	Ao dividir a comunicação em pequenos blocos (pacotes), o método de entrega de dados é muito mais eficiente.

IP Address
Um endereço IP (Internet Protocol) é um número exclusivo atribuído a um host em uma rede.
•	Os hosts usam esses números para tratar da comunicação em rede.
•	
Mask
Também chamada de máscara de rede, máscara de sub-rede ou máscara, uma máscara de rede é um sistema numérico que pode ser usado para definir quais endereços IP são considerados validos dentro de uma única rede.
•	Por causa de como os roteadores executam suas funções, as redes precisam ser claramente definidas.

Hostname
Cada host em uma rede pode ter seu próprio nome de host, porque os nomes são mais naturais para os humanos se lembrarem do que os números, facilitando o endereçamento de pacotes de rede para outro host.
•	Os nomes de host são traduzidos em endereços IP antes do envio do pacote de rede.

URL
Um URL (Uniform Resource Locator), também chamado de endereço da Web, é usado para localizar um recurso, como uma página da Web, na Internet.
•	É o que você digita no seu navegador para acessar uma página da web.
•	Por exemplo:
◦	http://www.netdevgroup.com.
◦	Ele inclui o protocolo http:// e o nome do host www.netdevgroup.com .


DHCP
Os hosts podem receber nomes de host, endereços IP e outras informações relacionadas à rede por um servidor DHCP (Dynamic Host Configuration Protocol) .
•	No mundo dos computadores, um protocolo é um conjunto de regras bem definido.
•	O DHCP define como as informações de rede são atribuídas aos hosts clientes, e o servidor DHCP é a máquina que fornece essas informações.

DNS	
Como mencionado anteriormente, os nomes de host são convertidos em endereços IP, antes do envio do pacote de rede.
•	Portanto, seu host precisa saber o endereço IP de todos os outros hosts com os quais você está se comunicando.
•	Ao trabalhar em uma rede grande (como a Internet), isso pode representar um desafio, pois há muitos hosts.
•	Um sistema de nomes de domínio (DNS) fornece o serviço de conversão de nomes de domínio em endereços IP.
•	Sistema de nomes de domínio (DNS)
◦	Freqüentemente, o endereço IP do servidor DNS é descoberto durante a solicitação DHCP, enquanto um computador está recebendo informações importantes de endereçamento para se comunicar na rede.
•	O endereço do servidor DNS é armazenado no arquivo
◦	/etc/resolv.conf.
•	Um arquivo /etc/resolv.conf típico é gerado automaticamente e se parece com o seguinte:
◦	cat /etc/resolv.conf                     
◦	nameserver 127.0.0.1
•	A configuração nameserver geralmente é definida como o endereço IP do servidor DNS.
•	O exemplo a seguir usa o comando host, que funciona com o DNS para associar um nome de host a um endereço IP.
•	Observe que o servidor de exemplo está associado ao endereço IP 192.168.1.2 pelo servidor DNS:
•	Também é comum ter várias configurações nameserver, caso um servidor DNS não esteja respondendo.
•	Arquivos de configuração de rede
◦	Resolução de nomes em um host Linux é realizado por 3 arquivos críticos:
◦	Os arquivos
▪	/etc/hosts
▪	/etc/resolv.conf
▪	e /etc/nsswitch.conf.
◦	Juntos, eles descrevem o local das informações do serviço de nomes, a ordem na qual os recursos são verificados e para onde procurar essas informações.
•	/etc/hosts
◦	Este arquivo contém uma tabela de nomes de host para endereços IP.
◦	Pode ser usado para complementar um servidor DNS.
▪	sysadmin@localhost:~ $ cat /etc/hosts  
▪	127.0.0.1 localhost
◦	Alguns nomes comuns no arquivo /etc/hosts são localhost e localhost.localdomain usados para se referir à máquina atual.
•	/etc/resolv.conf
◦	Este arquivo contém os endereços IP dos servidores de nomes que o sistema deve consultar em qualquer tentativa de resolver nomes para endereços IP.
◦	Esses servidores geralmente são servidores DNS.
◦	Também pode conter palavras-chave e valores adicionais que podem afetar o processo de resolução.
▪	sysadmin@localhost:~ $ cat /etc/resolv.conf  
▪	nameserver 127.0.0.11
•	/etc/nsswitch.conf
◦	Este arquivo pode ser usado para modificar onde ocorrem as pesquisas de nome de host.
◦	Ele contém uma entrada específica que descreve em que fontes de resolução de nomes de pedidos são consultadas.
▪	sysadmin @ localhost:~ $ cat /etc/nsswitch.conf
▪	# /etc/nsswitch.conf
▪	#
▪	Saída omitida ...
▪	hosts: files dns
▪	Saída omitida
•	O arquivo /etc/hosts é pesquisado primeiro, o servidor DNS em segundo:
◦	hosts: arquivos dns
•	O servidor DNS seria pesquisado primeiro, os arquivos locais em segundo:
◦	hosts: arquivos dns
•	Comandos ou programas no sistema, como o navegador, solicitam uma conexão com um computador remoto pelo nome DNS.
•	Em seguida, o sistema consulta vários arquivos em uma ordem específica para tentar resolver esse nome em um endereço IP utilizável.
•	Primeiro, o arquivo /etc/nsswitch.conf é consultado:
◦	hosts: arquivos dns
◦	Essa linha indica que o sistema deve consultar os arquivos locais primeiro na tentativa de resolver nomes de host, o que significa que o arquivo /etc/hosts será analisado para uma correspondência com o nome solicitado.
•	Segundo, o sistema consultará o arquivo /etc/hosts para tentar resolver o nome.
◦	Se o nome corresponder a uma entrada /etc/hosts, ele será resolvido.
◦	Não fará failover (ou continuará) na opção DNS, mesmo se a resolução for imprecisa.
◦	Isso pode ocorrer se a entrada /etc/hosts apontar para um endereço IP não atribuído.
•	Terceiro, se o arquivo local /etc/hosts não resultar em uma correspondência, o sistema usará as entradas do servidor DNS configuradas contidas no arquivo /etc/resolv.conf para tentar resolver o nome.
•	O arquivo /etc/resolv.conf deve conter pelo menos duas entradas para servidores de nomes, como o arquivo de exemplo abaixo:
◦	nameserver 10.0.2.3
◦	nameserver 10.0.2.4
•	O sistema de resolução de DNS usará o primeiro servidor de nomes para uma tentativa de pesquisa do nome.
•	Se isso não estiver disponível ou se for atingido um tempo limite, o segundo servidor será consultado quanto à resolução do nome.
•	Se uma correspondência for encontrada, ela retornará ao sistema e será usada para iniciar uma conexão e também será colocada no cache DNS por um período configurável.
Considere isto
Duas outras palavras-chave podem aparecer no arquivo /etc/resolv.conf do sistema.
Eles são rotineiramente incluídos nos arquivos padrão /etc/resolv.conf e, portanto, incluímos explicações sobre estes termos abaixo:
•	domain
◦	Seguido por um domínio qualificado, como snowblower.example.com, permite que a consulta para o host polarisse ja tentada tanto quanto o host polarisou, na sua falta, anexando o restante do nome de domínio a ele e, esperançosamente, resolvendo-o pelo servidor como esse nome (por exemplo, polaris.snowblower.example.com.)
•	search	
◦	Seguido por um conjunto de domínios separados que podem ser consultados um após o outro, esperançosamente, para resolver o nome.

Ethernet	
Em um ambiente de rede com fio, a Ethernet é a maneira mais comum de conectar fisicamente os hosts a uma rede.
•	Os cabos Ethernet estão conectados às placas de rede que suportam conexões Ethernet.
•	Os cabos e dispositivos Ethernet (como roteadores) são projetados especificamente para oferecer suporte a diferentes velocidades de comunicação, sendo a menor de 10 Mbps (10 Megabits por segundo) e a mais alta de 100 Gbps (100 gigabits por segundo).
•	As velocidades mais comuns são 100 Mbps e 1 Gbps.

TCP / IP	
O Protocolo de Controle de Transmissão / Protocolo da Internet (TCP / IP) é um nome sofisticado para uma coleção de protocolos (lembre-se, protocolo = conjunto de regras) que são usados para definir como a comunicação de rede deve ocorrer entre os hosts.
•	Embora não seja a única coleção de protocolos usados para definir a comunicação em rede, é a mais utilizada.
•	Como exemplo, o TCP / IP inclui a definição de como os endereços IP e as máscaras de rede funcionam.

IP Addresses
Como mencionado anteriormente, os hosts endereçam pacotes de rede usando o endereço IP da máquina de destino.
•	O pacote de rede também inclui um endereço de retorno , que é o endereço IP da máquina remetente.
•	De fato, existem dois tipos diferentes de endereços IP: IPv4 e IPv6 .
•	Por muitos anos, a técnica de endereçamento IP usada por todos os computadores foi o Ipv4.
◦	Em um endereço IPv4, um total de quatro números de 8 bits são usados para definir o endereço.
◦	Este é considerado um endereço de 32 bits (4 x 8 = 32).
▪	Por exemplo:
•	192.168.10.120
◦	8 bits refere-se a números de 0 a 255.
◦	Cada host na Internet deve ter um endereço IP exclusivo.
◦	Em um ambiente IPv4, há um limite técnico de cerca de 4,3 bilhões de endereços IP.
◦	Embora pareça que deve haver muitos endereços IP para circular, vários fatores levaram a um problema:
▪	A Internet começou a ficar sem endereços IP.
•	Essa questão incentivou o desenvolvimento do Ipv6.
◦	O IPv6 foi criado oficialmente em 1998.
◦	Em uma rede IPv6, os endereços são muito maiores, endereços de 128 bits que se parecem com isso:
▪	2001: 0db8: 85a3: 0042: 1000: 8a2e: 0370: 7334
◦	Essencialmente, isso fornece um pool de endereços muito maior, tão grande que a falta de endereços a qualquer momento no futuro próximo é muito improvável.
•	É importante observar que a diferença entre IPv4 e IPv6 não é apenas um pool de endereços maior.
•	O IPv6 possui muitos outros recursos avançados que abordam algumas das limitações do IPv4, incluindo melhor velocidade, gerenciamento de pacotes mais avançado e transporte de dados mais eficiente.
•	Considerando todas as vantagens, você pensaria que agora todos os hosts já usariam o Ipv6.
•	No entanto, a maioria dos dispositivos conectados à rede no mundo ainda usa IPv4 (algo como 98-99% de todos os dispositivos).
•	Então, por que o mundo não adotou a tecnologia superior do Ipv6?
•	Existem basicamente duas razões:
◦	NAT:
▪	Inventada para superar a possibilidade de ficar sem endereços IP em um ambiente IPv4, a NAT (Net Address Translation) utilizou uma técnica para fornecer mais hosts à Internet.
▪	Em poucas palavras, um grupo de hosts é colocado em uma rede privada sem acesso direto à Internet; um roteador especial fornece aceso à Internet e somente esse roteador precisa de um endereço IP para se comunicar na Internet.
▪	Em outras palavras, um grupo de hosts compartilha um único endereço IP, o que significa que muito mais computadores podem se conectar à Internet.
▪	Esse recurso significa que a necessidade de mudar para o IPv6 é menos crítica do que antes da invenção do NAT.
◦	Porting:
▪	Porting está mudando de uma tecnologia para outra.
▪	O IPv6 possui muitos novos recursos excelentes, mas todos os hosts precisam poder utilizá-los.
▪	Fazer com que todos na Internet (ou mesmo apenas alguns) façam essas mudanças representa um desafio. 
•	Quando você está configurando dispositivos de rede, há duas perguntas iniciais que você precisa fazer:
◦	Cabeado ou Wireless?
▪	A configuração de um dispositivo sem fio é um pouco diferente da configuração de um dispositivo com fio devido a alguns dos recursos adicionais normalmente encontrados em dispositivos sem fio (como segurança).
◦	DHCP ou Endereço estático?
▪	Lembre-se de que um servidor DHCP fornece informações de rede, como seu endereço IP e máscara de sub-rede.
▪	Se você não usar um servidor DHCP, precisará fornecer essas informações manualmente ao seu host, chamado usando um endereço IP estático.
•	De um modo geral, as máquinas de desktop usam redes com fio, enquanto os laptops usam redes sem fio.
•	Normalmente, uma máquina com fio usa um endereço IP estático, mas também pode ser atribuído através de um servidor DHCP.
•	Em quase todos os casos, as máquinas sem fio usam DHCP, pois quase sempre são móveis e conectadas a redes diferentes.

•	Arquivo de configuração IPv4 principal\
◦	O arquivo de configuração principal para uma interface de rede IPv4 é o arquivo:
▪	/etc/sysconfig/network-scripts/ifcfg-eth0.
◦	Se os dispositivos foram configurados para ser um cliente DHCP, o valor BOOTPROTO seria configurado para DHCP, e os valores das IPADDR, GATEWAY e  DNS não seria definida.

•	Arquivo de configuração IPv6 principal
◦	Em um sistema CentOS, o arquivo de configuração IPv6 principal é o mesmo arquivo em que a configuração IPv4 é armazenada:
▪	o arquivo /etc/sysconfig/network-scripts/ifcfg-eth0
◦	Se você deseja que seu sistema tenha um endereço IPv6 estático, adicione o seguinte ao arquivo de configuração:
▪	IPV6INIT = yes
▪	IPV6ADDR = <Endereço IP IPv6>
▪	IPV6_DEFAULTGW = <Endereço do gateway IP IPv6>
◦	Se você deseja que seu sistema seja um cliente DHCP IPv6, adicione a seguinte configuração:
▪	DHCPV6C = yes
◦	Você também precisa adicionar a seguinte configuração ao arquivo:
▪	/etc/sysconfig/network
•	NETWORKING_IPV6 = yes
Considere isto
O método amplamente aceito de fazer alterações em uma interface de rede é desativar a interface usando um comando, como ifdown eth0, fazer as alterações desejadas no arquivo de configuração e, em seguida, colocar a interface de volta em serviço com um comando como ifup eth0.
Outro método menos específico é reiniciar completamente a rede do sistema, com um comando como o service network restart que remove TODAS as interfaces, relê todos os arquivos de configuração relacionados e reinicia a rede do sistema.
Reiniciar o serviço de rede pode atrapalhar muito mais do que apenas a interface única que um usuário deseja alterar; portanto, use os comandos mais limitados e específicos para reiniciar a interface, se possível.


COMANDOS DE ADMINISTRACAO DE REDE.

ifconifg
Significa “configuracao da interface” e e usado  para exibir informacoes de configuracao de rede.
•	Sua sintaxe e a seguinte:
◦	ifconfig [OPCOES]
◦	O lo dispositivo é referido como o dispositivo de auto–retorno.
▪	É um dispositivo de rede especial usado pelo sistema ao enviar dados baseados em rede para si próprio.
◦	O comando  (ifconfig) também pode ser usado para modificar temporariamente as configurações de rede.
◦	Normalmente, essas alterações devem ser permanentes; portanto, o uso do comando ifconfig para fazer essas alterações é relativamente raro.
◦	O comando ifconfig está se tornando obsoleto em algumas distribuições Linux (descontinuado) e está sendo substituído por uma forma de comando ip, especificamente ip addr show.
◦	A saída do comando ifconfig mostra dois blocos principais de informação.
▪	O primeiro bloco, recuado por eth0, reflete informações sobre sua primeira placa de rede Ethernet.
▪	O segundo bloco, recuado por lo, reflete informações sobre o loopback ou a interface de rede interna.
▪	A segunda linha em cada bloco contém as informações pertinentes para a versão 4 do Protocolo da Internet (chamada IPv4), enquanto a terceira linha possui as informações para a versão 6 do Protocolo da Internet (IPv6).
▪	O IPv4 é um método mais antigo de identificar máquinas com uma série de números.
▪	Ainda é amplamente utilizado hoje, apesar do método IPv6 aprimorado estar disponível há muitos anos.
▪	Os endereços IPv4 são exibidos como quatro números decimais, variando de 0 até 255 separados por pontos.
▪	Os endereços IPv6 são números de 128 bits que são exibidos como dígitos hexadecimais que variam de 0 até f.
▪	Os dígitos hexadecimais são geralmente organizados em grupos de quatro dígitos separados por dois pontos.
▪	Se vários dígitos hexadecimais consecutivos tiverem o valor zero, eles serão substituídos por dois pontos.

iwconfig
Semelhante ao ifconfig porem dedicado as interfaces de redes sem fio (wifi).

ping
Comando usado para para verificar a conectividade entre dois dispositivos.
•	O comando ping pode ser usado para determinar se outra máquina está acessível.
•	Se o comando ping puder enviar um pacote de rede para outra máquina e receber uma resposta, você poderá se conectar a essa máquina.
•	Por padrao o comando ping continuara enviado pacotes infinitamente ate que a opção break seja inserida.
Para limitar quantos pings enviar, use a  opção (-c) seguida por um número indicando quantas iterações você deseja.
•	Opcoes utilizadas.
◦	Opcoes:	Significados:
▪	-c		Limita o numero de pings a serem enviados.
•	É importante observar que, apenas porque o comando ping falha, não significa que o sistema remoto esteja inacessível.
•	Alguns administradores configuram suas máquinas (e até redes inteiras!) para não responder às solicitações de ping porque um servidor pode ser atacado por algo chamado ataque de negação de serviço.
◦	Nesse tipo de ataque, um servidor é sobrecarregado por um grande número de pacotes de rede.
•	Ao ignorar solicitações ping, o servidor fica menos vulnerável.
•	Como resultado, o comando ping pode ser útil para verificar a disponibilidade de máquinas locais, mas nem sempre para máquinas fora da sua própria rede.
Considere isto
Muitos administradores usam o comando ping com um nome de host e, se isso falhar, use o endereço IP para verificar se a falha está na solução do nome do host do dispositivo.
Usar o nome do host primeiro economiza tempo; se esse comando ping for bem-sucedido, há uma resolução de nome adequada e o endereço IP também está funcionando corretamente.

ip
O comando ip difere de várias maneiras importantes do ifconfig, principalmente por meio de sua funcionalidade e conjunto de opções aprimoradas, que quase pode ser um balcão único para configuração e controle da rede de um sistema.
•	O formato para o comando ip é o seguinte:
◦	COMANDO DE OBJETOS ip [OPTIONS]
•	Embora o comando ifconfig esteja limitado principalmente à modificação dos parâmetros de rede e à exibição dos detalhes de configuração dos componentes de rede, o comando ip se ramifica para realizar parte do trabalho de vários outros comandos herdados, como route e arp.
Nota:
Os comandos Linux e Unix geralmente não desaparecem quando se tornam obsoletos; eles permanecem como um comando legado, às vezes por muitos anos, como o número de scripts que dependem desses comandos e a quantidade de memória muscular entre os administradores de sistema, sendo uma boa ideia mantê-los por motivos de compatibilidade
•	O comando ip pode inicialmente parecer um pouco mais detalhado que o comando ifconfig , mas é uma questão de fraseado e resultado da filosofia por trás da operação do comando ip.
•	Ambos mostram o tipo de interface, protocolos, hardware e endereços IP, máscaras de rede e várias outras informações sobre cada uma das interfaces ativas no sistema.

route
Lembre-se de que um roteador (ou gateway) é uma máquina que permite que hosts de uma rede se comuniquem com outra rede.
•	Para visualizar uma tabela que descreve para onde os pacotes de rede são enviados, use o comando route:
◦	root@localhost:~# route                                             
◦	Tabela de roteamento IP do kernel                                             
◦	Gateway de destino Flags Genmask Flags Ref Use Iface 192.168.1.0 * 255.255.255.0 UG 0 0 0 eth0  
◦	padrão 192.168.1.1  0.0.0.0 U 0 0 0 eth0
•	A primeira linha destacada no exemplo anterior indica que qualquer pacote de rede enviado para uma máquina na rede 192.168.1 não é enviado para uma máquina de gateway (isso indica que não há gateway).
•	A segunda linha destacada indica que todos os outros pacotes de rede são enviados ao host com o endereço IP 192.168.1.1(do roteador).
•	Alguns usuários preferem exibir essas informações apenas com dados numéricos, usando a opção (-n) do comando route
◦	Por exemplo, observe o seguinte e concentre-se em onde a saída costumava exibir o padrão:
▪	O 0.0.0.0 refere-se a todas as outras máquinas e é o mesmo padrão.
•	O comando route está se tornando obsoleto em algumas distribuições Linux (descontinuado) e está sendo substituído por uma forma de comando ip, especificamente ip route show.

netstat
O comando netstat é uma ferramenta poderosa que fornece uma grande quantidade de informações de rede.
•	Ele pode ser usado para exibir informações sobre conexões de rede, além de exibir a tabela de roteamento semelhante ao comando route.
•	Por exemplo, para exibir estatísticas sobre o tráfego de rede, use a opção (-i) para o comando netstat:
◦	root@localhost:~# netstat -i                                                  
◦	Tabela de interface do kernel
◦	Iface MTU encontrou  RX-OK  RX-ERR  RX-DRP  RX-OVR    TX-OK  TX-ERR   
TX-DRP   TX-OVR Flg
◦	eth0 1500 0 137 0 4 0   12 0    0 0 BMRU para 65536 0 18 0 0 0    18 0   0 0 LRU
•	As estatísticas mais importantes da saída acima são TX-OK e TX-ERR.
•	Uma alta porcentagem de TX-ERR pode indicar um problema na rede, como muito tráfego na rede.
•	Para usar o comando netstat para exibir informações de roteamento, use a opção (-r):
◦	root@localhost:~# netstat -r                                                  
◦	Tabela de roteamento de IP do kernel                                                       
◦	Gateway de destino Bandeiras de máscara de máscara Janela MSS irtt Iface
◦	192.168.1.0 * 255.255.255.0  U  0 0 0  eth0
◦	padrão 192.168.1.1  0.0.0.0  UG  0 0 0 eth0
•	O comando netstat também é comumente usado para exibir portas abertas.
•	Uma porta é um número exclusivo associado a um serviço fornecido por um host.
•	Se a porta estiver aberta, o serviço estará disponível para outros hosts.
•	Por exemplo, você pode efetuar login em um host de outro host usando um serviço chamado SSH.
◦	O serviço SSH está atribuído à porta nº 22.
◦	Portanto, se a porta 22 estiver aberta, o serviço estará disponível para outros hosts.
•	É importante observar que o host também precisa ter os serviços em execução; isso significa que o serviço (neste caso, o daemon ssh) que permite que usuários remotos efetuem login precisa ser iniciado (o que normalmente é, na maioria das distribuições Linux).
•	Para ver uma lista de todas as portas abertas no momento, use o seguinte comando netstat -tln:
◦	root @ localhost : ~ # netstat -tln
◦	Conexões ativas à Internet (apenas servidores)                                    
◦	Proto	Recv-Q	Send-Q	Endereço local	Estado do endereço externo     
◦	tcp	0		0           	192.168.1.2:53 	0.0.0.0:* ESCUTE    
◦	tcp	0             	0           	127.0.0.1:53 		0.0.0.0:* LISTEN    
◦	tcp	0             	0           	0.0.0.0:22 		0.0.0.0:* LISTEN    
◦	tcp       0             	0           	127.0.0.1:953 		0.0.0.0:* LISTEN    
◦	tcp6     0             	0           	::: 53 			:::* LISTEN    
◦	tcp6     0             	0 		: ::22                  	::: *LISTEN    
◦	tcp6     0             	0 		:: 1: 953 		::: * LISTEN    
•	Como você pode ver na saída acima, a porta 22 está escutando, o que significa que está aberta.
•	No exemplo anterior, significa (-t) TCP, (-l) LISTEN significa ouvindo (quais portas estão ouvindo) e (-n) representa números de show, não nomes .
•	Às vezes, mostrar os nomes pode ser mais útil.
•	Isso pode ser conseguido descartando a opção (-n):
◦	root @ localhost : ~ # netstat -tl
◦	Conexões ativas à Internet (apenas servidores)                                      
◦	Proto	Recv-Q 	Send-Q 	Endereço local 	Endereço externo Estado     
◦	tcp 	0 		0 		cserver.example.	:domain *: * LISTEN    
◦	tcp 	0 		0 		localhost: 		domain *: * LISTEN    
◦	tcp 	0 		0 		*: ssh 			*: * LISTEN    
◦	tcp 	0 		0 		host local: 953 	*: * LISTEN    
◦	tcp6	 0 		0 		[::]: domain 		[::]: * LISTEN    
◦	tcp6	 0 		0 		[::]: ssh 		[::]: * LISTEN     
◦	tcp6	 0 		0 		localhost: 953 		[::]: * LISTEN    
•	Em algumas distribuições, você pode ver a seguinte mensagem na página de manual do comando netstat:
NOTA
Este programa está obsoleto.
A substituição para netstat é ss .
A substituição do netstat -r é ip route.
A substituição do netstat -i é o link ip -s .
A substituição para netstat -g é ip maddr .
•	Embora nenhum outro desenvolvimento esteja sendo feito no comando netstat, ele ainda é uma excelente ferramenta para exibir informações da rede.
•	O objetivo é eventualmente substituir o comando netstat por comandos como os comandos ss e ip.
•	No entanto, é importante perceber que isso pode levar algum tempo.

ss
O comando ss foi projetado para mostrar estatísticas de soquete e suporta todos os principais tipos de pacotes e soquetes.
•	Pretendia substituir e ser semelhante em função ao comando netstat, também mostra muito mais informações e possui mais recursos.
•	O principal motivo pelo qual um usuário usaria o comando ss é visualizar quais conexões são estabelecidas atualmente entre a máquina local e remota, estatísticas sobre essas conexões etc.
•	Semelhante ao comando netstat, você pode obter muitas informações úteis do comando ss por si só, como mostra o exemplo abaixo.
◦	root @ localhost : ~ # ss
◦	Endereço Local de Recv-Q do Estado Netid:    Endereço de Ponto de Porta:    Porta
◦	u_str ESTAB 0 0 * 104741 * 104740
◦	u_str ESTAB 0 0 / var / run / dbus / system_bus_socket 14623 *  
◦	14606 u_str ESTAB 0 0 / var / run / dbus / system_bus_socket 13582 * 13581  
◦	u_str ESTAB 0 0 / var / run / dbus / system_bus_socket 16243 * 16242  
◦	u_str ESTAB 0 0 * 16009 * 16010  
◦	u_str ESTAB 0 0 / var / run / dbus / system_bus_socket 10910 * 10909  
◦	u_str ESTAB 0 0 @ / tmp / dbus-LoJW0hGFkV 15706 * 15705   
◦	u_str ESTAB 0 0 * 24997 * 24998   
◦	u_str ESTAB 0 0 * 16242 * 16243   
◦	u_str ESTAB 0 0 @ / tmp / dbus-opsTQoGE 15471 * 15470   
•	A saída é muito semelhante à saída do comando netstat sem opções.
•	As colunas acima são:
◦	Netid - O tipo de soquete e protocolo de transporte\
◦	State - Conectado ou Desconectado, dependendo do protocolo
◦	Recv-Q - Quantidade de dados na fila para processamento sendo recebidos
◦	Send-Q - Quantidade de dados na fila para serem enviados para outro host
◦	Local Address - O endereço e a porta da parte da conexão do host local
◦	Peer Address - Porta	
•	O formato da saída do comando ss pode mudar drasticamente, dadas as opções especificadas, como o uso da opção (-s), que exibe principalmente os tipos de soquetes, estatísticas sobre sua existência e número de pacotes reais enviados e recebidos por cada tipo de soquete, como mostrado abaixo:
◦	root @ localhost : ~ # ss -s
◦	Total: 1000 (kernel 0)
◦	TCP: 7 (estab 0, fechado 0, órfão 0, synrecv 0, timewait 0/0), portas 0
◦	Transporte Total IP Ipv6
◦	* 0 - -        
◦	RAW 0 0 0        
◦	UDP 9 6 3        
◦	TCP 7 3 4        
◦	INET 16 9 7        
◦	FRAG 0 0 0    
•	Embora o comando ss ofereça muitas opções diferentes para coletar e exibir informações, os exemplos acima são os mais comuns

dig
Pode haver momentos em que você precise testar a funcionalidade do servidor DNS que seu host está usando.
•	Uma maneira de fazer isso é usar o comando dig, que executa consultas no servidor DNS para determinar se as informações necessárias estão disponíveis no servidor.
•	No exemplo a seguir, o comando dig é usado para determinar o endereço IP do host example.com:
◦	root @ localhost : ~ # dig example.com                                              
◦	; << >> DiG 9.8.1-P1 << >> example.com                                          
◦	;; opções globais: + cmd                                                       
◦	;; Resposta obtida:                                                                
◦	;; - >> HEADER << - opcode: QUERY, status: NOERROR, id: 45155                     
◦	;; sinalizadores: qr aa rd ra; CONSULTA: 1, RESPOSTA: 1, AUTORIDADE: 1, ADICIONAL: 0                                                                                     
◦	;; SEÇÃO DA PERGUNTA:;  example.com. EM UM                                                                                                                   
◦	;; SEÇÃO DE RESPOSTA:  example.com. 86400 IN A 192.168.1.2
◦	; SEÇÃO DE AUTORIDADE:    example.com. 86400 NO NS example.com.                  
◦	;; Tempo de consulta: 0 mseg                                                          
◦	;; SERVIDOR: 127.0.0.1 # 53 (127.0.0.1)                                             
◦	;; QUANDO: ter 8 de dezembro 17:54:41 2015                                              
◦	;; TAMANHO MSG rcvd: 59  
•	Observe que a resposta incluiu o endereço IP de 192.168.1.2, o que significa que o servidor DNS possui o endereço IP para informações de conversão de nome de host em seu banco de dados.
•	Se o servidor DNS não tiver as informações solicitadas, ele está configurado para solicitar outros servidores DNS.
•	Se nenhum deles tiver as informações solicitadas, uma mensagem de erro será exibida:
◦	root @ localhost : ~ # dig sample.com                                            
◦	; << >> DiG 9.8.1-P1 << >> sample.com                                           
◦	;; opções globais: + cmd
◦	;; a conexão expirou; nenhum servidor pode ser alcançado

host
Na sua forma mais simples, o comando host trabalha com o DNS para associar um nome de host a um endereço IP.
•	Conforme usado no exemplo anterior, example.com está associado ao endereço IP de 192.168.1.2:
◦	root @ localhost : ~ # host
◦	example.com                                            
◦	example.com tem o endereço 192.168.1.2   
•	O comando host também pode ser usado ao contrário, se um endereço IP for conhecido, mas o nome do domínio não.
◦	root @ localhost : ~ # host 192.168.1.2                                            
◦	2.1.168.192.in-addr.arpa ponteiro de nome de domínio example.com.                     
◦	2.1.168.192.in-addr.arpa ponteiro de nome de domínio cserver.example.com.   
•	Existem outras opções para consultar os vários aspectos de um DNS, como um CNAME nome canônico -alias :
◦	root @ localhost : ~ # host -t CNAME example.com                                   
◦	example.com não possui registro CNAME
•	Como muitos servidores DNS armazenam uma cópia de example.com, os registros SOA Start of Authority indicam o servidor principal do domínio:
◦	root @ localhost : ~ # host -t SOA example.com                                     
◦	example.com possui registro SOA example.com. cserver.example.com. 2 604800 86400 2419200 60480
•	Uma lista abrangente de informações de DNS sobre example.com pode ser encontrada usando a opção (-a) all :
◦	root @ localhost : ~ # host -a example.com                                         
◦	Tentando "example.com"                                                          
◦	;; - >> HEADER << - opcode: QUERY, status: NOERROR, id: 3549                      
◦	;; sinalizadores: qr aa rd ra; CONSULTA: 1, RESPOSTA: 3, AUTORIDADE: 0, ADICIONAL: 1                                                                          
◦	;; SEÇÃO DA PERGUNTA:;   \
◦	example.com. EM QUALQUER
◦	;; SEÇÃO DE RESPOSTA:    
◦	example.com. 86400 EM SOA example.com. cserver.example.com. 2 604800 86400 2419200 604800  example.com. 86400 NO NS example.com.example.com. 86400 IN A 192.168.1.2  
◦	; SEÇÃO ADICIONAL:
◦	example.com. 86400 IN A 192.168.1.2   
◦	Recebido 119 bytes de 127.0.0.1 # 53 em 0 ms

ssh
O comando ssh permite que você se conecte a outra máquina na rede, efetue login e execute tarefas na máquina remota.
•	Se você fornecer apenas um nome de máquina ou endereço IP para fazer login, o comando ssh pressupõe que você deseja fazer login usando o mesmo nome de usuário em que você está conectado atualmente.
•	Para usar um nome de usuário diferente, use a sintaxe:
◦	nome de usuário @ hostname
▪	root @ localhost : ~ # ssh bob @ test
▪	Não é possível estabelecer a autenticidade do host 'test (127.0.0.1)'.
▪	A impressão digital da chave RSA é c2: 0d: ff: 27: 4c: f8: 69: a9: c6: 3e: 13: da: 2f: 47: e4: c9.
▪	Tem certeza de que deseja continuar a conexão (sim / não)? Sim
▪	Aviso: 'teste' (RSA) adicionado permanentemente à lista de hosts conhecidos.
▪	Senha do bob @ test : bob @ test : ~ $ date
▪	Sex Out 4 16:14:43 CDT 2013   
•	Para retornar à máquina local, use o comando exit:
◦	bob @ test : ~ $ exit
◦	logout
◦	Conexão para o teste fechado. root @ localhost :
Aviso:
Cuidado, se você usar o comando exit muitas vezes, fechará a janela do terminal em que está trabalhando!
•	Portas conhecidas são os números de porta no intervalo de 0 a 1023, normalmente usados pelos processos do sistema para fornecer serviços de rede.
•	Uma lista de nomes de serviço e números de porta associados pode ser encontrada no arquivo /etc/services.
Impressão digital da chave RSA
Ao usar o comando ssh, o primeiro prompt solicita que você verifique a identidade da máquina na qual está efetuando login.
Na maioria dos casos, você vai querer responder yes.
Embora você possa verificar com o administrador da máquina remota se a impressão digital da chave RSA está correta, esse não é o objetivo desta consulta.
Ele foi projetado para futuras tentativas de login.
Depois de responder yes, a impressão digital da chave RSA da máquina remota é armazenada no sistema local.
Quando você tenta usar ssh esta mesma máquina no futuro, a impressão digital da chave RSA fornecida pela máquina remota é comparada à cópia armazenada na máquina local.
Se eles corresponderem, o prompt do nome de usuário será exibido.
Se eles não corresponderem, um erro como o seguinte é exibido:
•	sysadmin @ localhost : ~ $ ssh bob @ test
•	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ @@@@@@@@@@@@@@@@
•	@ AVISO: A IDENTIFICAÇÃO DO HOST REMOTA FOI MUDADA! @
•	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ @@@@@@@
•	É POSSÍVEL QUE ALGUÉM ESTÁ FAZENDO ALGO DESAGRADÁVEL!
•	Alguém pode estar ouvindo você agora (ataque do meio do homem)!
•	Também é possível que a chave do host RSA tenha sido alterada.
•	A impressão digital da chave RSA enviada pelo host remoto é
•	c2: 0d: ff: 27: 4c: f8: 69: a9: c6: 3e: 13: da: 2f: 47: e4: c9.
•	Entre em contato com o administrador do sistema.
•	Adicione a chave do host correta em /home/sysadmin/.ssh/known_hosts para se livrar dessa mensagem.
•	Chave ofensiva em /home/sysadmin/.ssh/known_hosts:1 A
•	chave do host RSA para teste foi alterada e você solicitou uma verificação rigorosa.
•	Falha na verificação da chave do host.
Este erro pode indicar que um host não autorizado substituiu o host correto.
Verifique com o administrador do sistema remoto.
Se o sistema fosse reinstalado recentemente, ele teria uma nova chave RSA e isso causaria esse erro.
Caso essa mensagem de erro ocorra devido a uma reinstalação remota da máquina, você poderá remover o arquivo ~/.ssh/known_hosts do sistema local (ou apenas remover a entrada dessa máquina) e tentar conectar-se novamente:
•	sysadmin @ localhost : ~ $ cat ~ / .ssh / known_hosts
•	teste ssh-rsa AAAAB3NzaC1yc2EAAAAmIwAAAQEAklOUpkDHrfHY17SbrmTIp / RZ0V4DTxgq9wzd + ohy006SWDSGPA + nafzlHDPOW7vdI4mZ5ew18KL4JW9jbhUFrviQzM7xlELEVf4h9lFX5QVkbPppSrg0cda3Pbv7kOdJ / MTyBlWXFCRH + Cv3FXRitBqxiX1nKhXpHAZsMciLq8V6RjsNAQwdsdMFvSlVK / 7BA
•	t5FaiKoAfncM1Q8x3 + 2V0Ww71 / eIFmb1zuUFljHYTprrX88XypNDvjYNby6vw / Pb0rwprz / Tn
•	mZAW3UX + PnTPI89ZPmNBLuxyrD2cE86Z / il8b + gw3r3 + 1nJotmIkjn2so1d01QraTlMqVSsbx
•	NrRFi9wrf + ghw == sysadmin @ localhost : ~ $ rm ~ / .ssh / known_hosts
•	 sysadmin @ localhost : ~ $ ssh bob @ test
•	Não é possível estabelecer a autenticidade do host 'test (127.0.0.1)'.
•	A impressão digital da chave RSA é c2: 0d: ff: 27: 4c: f8: 69: a9: c6: 3e: 13: da: 2f: 47: e4: c9.
•	Tem certeza de que deseja continuar a conexão (sim / não)? sim
•	Aviso: 'teste' (RSA) adicionado permanentemente à lista de hosts conhecidos.
•	Senha do bob @ test:
•	Último login: Sex Out 4 16:14:39 CDT 2013 from localhost


SOBRE ARGUMENTOS ou GLOBBING

&& (duplo comercial)
Argumento usado para executar os comandos sequencialmente.
•	O Segundo comando so vai ser executado se o primeiro nao houver erro.

; (ponto e virgula)
Argumento usado para executar os comandos sequencialmente.
•	O segundo comando sera executado independentemente se houver erro no primeiro comando.

|| (duplo pipe)
Argumento usado para executar o comando de forma em que se o primeiro falhar o segundo sera executado.
•	Porem se houver exito no primeiro comando o segundo nao sera executado.


“ (Aspas Duplas):
As aspas duplas impedem o Shell de interpretar alguns metacaracteres (Caracteres especiais), incluindo caracteres glob.
•	Entre aspas duplas, um asterisco é apenas um asterisco, um ponto de interrogação é apenas um ponto de interrogação e assim por diante, o que é útil quando você deseja exibir algo na tela que normalmente é um caractere especial para o Shell.
•	As aspas duplas ainda permitem a substituição de comandos , a substituição de variáveis e outros metacaracteres de Shell que ainda não foram discutidos.

"As aspas ou backticks são usadas para especificar um comando em um comando, um processo chamado substituição de comando .
•	Isso permite o uso poderoso e sofisticado de comandos."

‘ (Aspas Simples):
Aspas simples impedem o Shell de interpretar caracteres especiais, incluindo globs, variáveis, substituição de comandos e outros metacaracteres que ainda não foram discutidos.
•	Por exemplo:
◦	Para fazer com que o caractere  ($) signifique simplesmente a ($), em vez de agir como um indicador para o Shell para procurar o valor de uma variável.

Caracteres Curingas (GLOBBING)

•	Carcater (*) asterisco.
◦	Usado para representar zero ou mais caracteres em um nome de arquivo.
◦	Pode ser utlizado para exibir arquivos comecados com uma letra especifica.
▪	Por exemplo:
•	 (sysadmin@localhost:~$ ls -d /etc/s*)
◦	 Exibira todos os arquivos comecados com "s" no caminho de:
▪	(sysadmin@localhost:~$ ls -d /etc/).
▪	Por exemplo:
•	Para exibir todos os arquivos no diretório (/etc) que começam com a letra "t":
◦	 (echo / etc / t*)
◦	Pode-se usar o caractere (*) asterisco em qualquer lugar  dentro do nome de arquivo.
▪	Por exemplo:
•	O seguinte padrão corresponde a qualquer nome de arquivo no diretório (/etc) que termina com (.d):
◦	(echo /etc/*.d)
◦	Tambem pode ser usado para exibir todos os arquivos que comecem com determinada letra e terminem com determinada extensao de arquivo.
▪	Por exemplo:
•	No diretório (/etc) que começam com a letra "r" e terminam com ".conf":
◦	(echo /etc/r*.conf)
◦	O asterisco (*) pode ser usado em qualquer lugar da string, e subistitui qualquer valor para que seja efetuado a pesquisa.

•	Caracter (?) interrogacao.
◦	O caracter de (?) interrogação representa qualquer caractere único.
◦	Cada caractere de ponto de interrogação corresponde exatamente a um caractere em um nome de arquivo.
▪	Suponha que você queira exibir todos os arquivos no diretório (/etc) que começam com a letra "t" e tenham exatamente 7 caracteres após o caractere "t":
•	(echo /etc/t???????)
◦	Pode ser utilizado para exibir arquivos com a quantidade de caracteres (?) digitados no comando.
▪	Por exemplo.
•	(sysadmin@localhost:~$ ls -d /etc/????)
◦	Exibira todos os arquivos com quatro caracteres, correspondente ao valor de (?) digitados no comando.

•	Os caracteres GLOBBING podem ser usados juntos para encontrar padrões ainda mais complexos.
◦	Por exemblo:
▪	O comando padrão:
•	(/etc/*????????????????????).
◦	Corresponde apenas aos arquivos no diretório (/etc) com vinte ou mais caracteres no nome do arquivo.
◦	O asterisco e o ponto de interrogação também podem ser usados juntos para procurar arquivos com extensões de três letras usando o padrão:
•	(/etc/*.???).
◦	Pense no padrão do caracter (?) como:
▪	"Corresponder nomes de arquivos que começam com" x numeros" de caracteres, depois possuem zero ou mais caracteres e terminam com um caractere de "tal letra".

•	Caracter entre ([]) colchetes
◦	Os caracteres entre colchetes são usados para corresponder a um único caractere, representando um intervalo de caracteres que são possíveis.
▪	Por exemplo.
•	O padrão (/etc/[gu]*)
◦	Corresponde a qualquer arquivo que comece com um caractere "g" ou "u" e contém zero ou mais caracteres adicionais.
◦	O caracter ([]) colchetes especifica um único caractere para corresponder a um conjunto de caracteres.
◦	Pode ser utilizado para exibir arquivos comecados com os valores digitados entre os colchetes.
▪	Por exemplo:
•	(sysadmin@localhost:~$ ls -d /etc/[abcd]*)
◦	Exibe todos os arquivos comecados com as letras a,b,c ou d.
◦	Os colchetes também podem ser usados para representar um intervalo de caracteres.
▪	Por exemplo:
•	O padrão (/etc/[a-d]*)
◦	Corresponde a todos os arquivos que começam com qualquer letra entre e incluindo a e d.
◦	O padrão (/etc/*[0-9]*)
▪	Exibe qualquer arquivo que contenha pelo menos um número.
◦	O intervalo é baseado na tabela de texto ASCII.
▪	Esta tabela define uma lista de caracteres, organizando-os em uma ordem padrão específica.
▪	Se um pedido inválido for fornecido, nenhuma correspondência será feita.
•	A tabela de texto ASCII pode ser visualizada executando o comando (ascii).
•	
•	Caracter (!) ponto de exclamacao.
◦	O caractere de ponto de exclamação é usado em conjunto com os colchetes para negar um intervalo.
▪	Por exemplo:
•	O padrão (/etc/[!DP]*)
◦	Corresponde a qualquer arquivo que não começar com um "D" ou "P".

"Se a opcao (-d) do comando (ls) for utlizado junto ao um "globbing de arquivos"(curingas) ele impedira que os subdiretorios sejam exibidos."


SOBRE EXPRESSOES REGULARES

Expressões regulares têm duas formas comuns:
•	Básica e Estendida.
◦	Expressoes regulares basicas:
▪	Expressões regulares, também conhecidas como regex , são uma coleção de caracteres normais e especiais que são usadas para encontrar padrões simples ou complexos, respectivamente, em arquivos.
▪	Esses caracteres são usados para executar uma função correspondente específica em uma pesquisa.
▪	Expressões regulares são "gananciosas" no sentido de corresponderem a todas as instâncias do padrão especificado:
▪	Para limitar a saída, você pode usar expressões regulares para especificar um padrão mais preciso.
•	Por exemplo:
◦	O caractere de sinal de intercalação (^) pode ser usado para corresponder a um padrão no início de uma linha; portanto, quando você executa a seguinte linha de comando, apenas as linhas que começam com root devem ser correspondidas e exibidas:
▪	(grep '^ root' passwd)
•	Melhores prática
◦	Use aspas simples (não aspas duplas) em torno de expressões regulares para impedir que o programa shell tente interpretá-las.
•	A maioria dos comandos que usam expressões regulares pode interpretar expressões regulares básicas.
•	No entanto, expressões regulares estendidas não estão disponíveis para todos os comandos e geralmente é necessária uma opção de comando para que funcionem corretamente.

•	A tabela a seguir resume os caracteres básicos da expressão regular:
◦	Caracter basico de Regex:	Significado:
▪	.				Qualquer caracter único.
▪	[ ] 				Qualquer caracter especificado.
▪	[^ ]				Nao e o caracter especificado.
▪	*				Zero ou mais caracteres anteriores
▪	^				Se o primeiro caracter do padrao, o padrao deve estar no inicio da linha para corresponder, caso contrario, a penas um literal ^.
▪	$				Se o ultimo caracter do padrao, o padrao deve estar no final da linha para corresponder, caso caso contrario, apenas um literal $.

•	A tabela a seguir resume as expressões regulares estendidas, que devem ser usadas com o comando egrep ou a opção -E com o comando grep.
◦	Caracter basico do Regex estendido		Significado.
▪	+						Um ou mais do padrao anterior.
▪	?						O padrao anterior e opcional
▪	{ }						Especifique correspondecias minimas, maximas ou exatas do padrao anterior.
▪	|						Alternacao – um “ou” logico.
▪	( )						Usado para criar grupos.

•	Use o símbolo ($) para corresponder ao padrão no final de uma linha:
◦	Corresponde apenas à instância no final da linha.
•	Use o caracter de ponto (.) para corresponder  a qualquer carecter unico.
◦	Por exemplo:
▪	Execute o seguinte comando para corresponder qualquer caractere seguido por `y`
•	grep '.y' passwd
•	 O caractere de canal (|), ou "operador de alternância",  atua como um operador "ou".
•	Use outra expressão regular estendida, desta vez egrep com alternância em um grupo para corresponder a um padrão. As strings nobe nao corresponderão:
◦	egrep 'no (b | n)' passwd
•	Os caracteres  ([ ])  também podem ser usados para corresponder a um único caractere.
◦	No entanto, diferentemente do caractere de ponto (.), os caracteres ([ ]) são usados para especificar exatamente qual caractere você deseja corresponder.
▪	Por exemplo:
•	Se você deseja combinar um caractere numérico, pode especificar [0-9].
◦	head passwd | grep '[0-9]'
•	Suponha que você queira procurar um padrão que contenha uma sequência de três dígitos. Você pode usar caracteres ({ }) com um número para expressar que deseja repetir um padrão um número específico de vezes;
◦	Por exemplo
▪	grep -E '[0-9] {3}' passwd
•	Existem Expressões regulares básicas (disponíveis para uma ampla variedade de comandos do Linux) e Expressões regulares estendidas (disponíveis para comandos mais avançados do Linux). Expressões regulares básicas incluem o seguinte:
◦	Personagem		Significado
▪	.			Qualquer caractere único
▪	[ ]			Uma lista ou intervalo de caracteres para corresponder a um caractere.
•	Se o primeiro caractere entre colchetes for o sinal de intercalação ^, significa qualquer caractere que não esteja na lista
▪	*			O caractere anterior repetiu zero ou mais vezes
▪	^			Se o primeiro caractere do padrão, o padrão deve estar no início da linha para corresponder, caso contrário, apenas um ^caractere literal
▪	$			Se o último caractere no padrão, o padrão deve estar no final da linha para corresponder, caso contrário, apenas um caractere $ literal.

•	Caracter (.) ponto
◦	Corresponde a qualquer caractere, exceto o novo caractere de linha.
▪	Exemplo:
•	(grep 'r..f' red.txt)
◦	O padrão r..f encontraria qualquer linha que contivesse a letra r seguida por exatamente dois caracteres e depois a letra f.
▪	O caractere de ponto pode ser usado qualquer número de vezes.
◦	Para encontrar todas as palavras que tenham pelo menos quatro caracteres, o seguinte padrão pode ser usado:
▪	Exemplo:
•	(grep '....' red.txt)
•	Caracter ([]) colchetes
◦	Ao usar o personagem (.),  qualquer personagem possível pode corresponder a ele. Em alguns casos, você deseja especificar exatamente quais caracteres deseja corresponder, como um alfabeto em minúsculas ou um número.
◦	Os colchetes ([ ]) correspondem a um único caractere da lista ou intervalo de caracteres possíveis contidos entre colchetes.
▪	Por exemplo:
•	cat arquivo.txt
◦	Para encontrar todas as linhas no arquivo.txt quais há um número, use o padrão [0123456789]ou [0-9]:
▪	grep '[0-9]' arquivo.txt  
▪	Cada caractere possível pode ser listado [abcd] ou fornecido como um intervalo [a-d], desde que o intervalo esteja na ordem correta.
•	Por exemplo:
◦	[d-a] nao funcionaria por que nao e um intervalo valido.
◦	E quanto à isenção de caracteres ?
▪	Por exemplo, para corresponder a um caractere que pode ser qualquer coisa, exceto um x, you z?
▪	Seria ineficiente fornecer um conjunto com todos os caracteres x, exceto , you z.
▪	Para corresponder a um caractere que não é um dos caracteres listados, inicie o conjunto com um símbolo (^).
▪	Para encontrar todas as linhas que contêm caracteres não numéricos, insira a  (^) como o primeiro caractere entre colchetes.
•	Esse personagem nega os caracteres listados:
◦	Exemplo:
▪	grep '[^0-9]' arquivo.txt
•	Não confunda [^0-9] com as linhas que não contêm números . Na verdade, corresponde a linhas que contêm  nao numeros .

•	Caractere (*) asterisco
◦	Usado para corresponder a zero ou mais ocorrências de um caractere ou padrão que o precede.
▪	Por exemplo:
•	(e*)
◦	Corresponderia a zero ou mais ocorrencias de letra e:
◦	Também é possível corresponder a zero ou mais ocorrências de uma lista de caracteres utilizando colchetes.
▪	O padrão [oe]* usado no exemplo a seguir corresponde a zero ou mais ocorrências do caractere ou do e-caractere:
•	(grep 'r[oe]*d' arquivo.txt)
◦	Quando usado com apenas um outro personagem, (*) não é muito útil. Qualquer um dos seguintes padrões corresponderia a cada sequência ou linha no arquivo: '.*' 'e*' 'b*' 'z*' porque o caractere asterisco (*) pode corresponder a zero ocorrências de um padrão.
◦	para tornar útil o caractere asterisco, é necessário criar um padrão que inclua mais do que apenas o caractere anterior
▪	Por exemplo:
•	Os resultados acima podem ser refinados adicionando outro e para fazer com que o padrão (ee*) corresponda efetivamente a cada linha que contém pelo menos uma e.
•	Exemplo:
◦	(grep 'ee*' arquivo.txt)
•	Caracteres ancora
◦	Caracteres âncora são uma das maneiras pelas quais expressões regulares podem ser usadas para restringir os resultados da pesquisa.
◦	Eles especificam se a correspondência ocorre no início ou no final da linha.
▪	Por exemplo,
•	O padrão root aparece  muitas vezes no arquivo /etc/passwd:
◦	(grep 'root' /etc/passwd)
▪	O caractere de circunflexo (circunflexo) ^é usado para garantir que um padrão apareça no início da linha.
•	Por exemplo,
◦	para encontrar todas as linhas /etc/passwd que começam com root use o padrão ^root.
▪	(grep '^root' /root/etc/passwd)
▪	O segundo caractere âncora ($) pode ser usado para garantir que um padrão apareça no final da linha, reduzindo efetivamente os resultados da pesquisa.
•	Para encontrar as linhas que terminam com um r no arquivo arquivo.txt, use o padrão 'r$':
◦	Mais uma vez, a posição desse personagem é importante.
◦	O ($) deve ser o último caractere no padrão para ser eficaz como uma âncora.
•	Barra invertida (\)
◦	Em alguns casos, convém corresponder um caractere que passa a ser um caractere especial de expressão regular.
◦	Para procurar um (*) caractere asterisco real , coloque um (\) caractere de barra invertida antes do (*) caractere asterisco:
•	Expressoes regulares estendidas.
◦	O uso de expressões regulares estendidas geralmente requer que uma opção especial seja fornecida ao comando para reconhecê-las.
◦	Historicamente, existe um comando chamado egrep, que é semelhante grep, mas pode entender expressões regulares estendidas.
◦	Agora, o comando egrep foi preterido em favor do uso grep com a opção -E\
▪	As seguintes expressões regulares são consideradas estendidas:
•	Caractere:      Significado:
•	?               		Corresponde ao caractere anterior zero ou uma vez, por isso é um caractere opcional
•	+              		 Corresponde ao caractere anterior repetido uma ou mais vezes
•	|               		Alteracao ou como um operador logio "ou".
◦	Por exemplo
▪	Para corresponder 'colou' seguido por zero ou um caractere ? seguirdo por um caractere r:
•	 (grep -E 'colou? r' arquivo.txt)
▪	Para corresponder a um ou mais 'e' caracteres:
•	(grep -E 'e+' arquivo.txt)
▪	Para corresponder a gray ou grey:
•	(grep -E 'gray | grey arquivo.txt

SOBRE VARIAVEIS

aptitude

env
Gera uma lista das variáveis de ambiente

export
Usado para transformar uma variável local em uma variável de ambiente.

unset
Usado para remover uma variavel.

echo
•	Usado para exibir a saída no terminal.
◦	Para exibir o valor da variável, use um caractere de cifrão seguido pelo nome da variável como argumento para o comando.
▪	(echo $COMANDO)
•	echo $HOME
◦	Comando para exibir a variavel $HOME
▪	Onde mostra o caminho para o diretorio inicial.

alias
Um alias pode ser usado para mapear comandos mais longos para sequências de teclas mais curtas.
•	Para evitar o uso de um alias:
◦	 Coloque um caracter de barra invertida (\) na frente do comando.

HISTSIZE
Variável que define quantos comandos anteriores armazenar na lista de histórico

PRUNEPATHS
Lista de caminhos de pastas separadas por um espaco em branco.
•	Define os diretorios  que serao ignorados na indexacao.

PRUNEFS
Lista de sistema de arquivos separados por um espaco em branco.
•	Identifica os tipos de particoes que sera ignoradas.
◦	Os sistemas de arquivos listados aqui serao ignorados, não serao escaneados.

PRUNENAMES
Lista de nomes de arquivos separados por um espaco em branco.
•	Esses nomes serao ignorados por updatedb

PRUNE_BIND_MOUNTS
Pode receber os valores 0 (no) ou 1 (yes).
•	Se o valor for 1 ou yes:
◦	bind mounts não são escaneados por updatedb.


inode
Número de identificador exclusivo atribuído a cada arquivo.
•	De modo geral, o inode e a identidade de um arquivo ou diretorio, e uma  identificacao única para ele.
◦	Ao ler qualquer arquivo ou diretorio, o kernel trata de ler primeiriamente o INODE do arquivo para depois chegar ao arquivo de fato.



SOBRE REDIRECIONAMENTO


O redirecionamento de entrada / saída (E / S) permite que as informações da linha de comando sejam passadas para diferentes fluxos.
•	Quando se trata de comando de entrada e saída, existem três caminhos, ou "trilhas".
◦	Esses caminhos são chamados de descritores de arquivo.
•	O primeiro descritor de arquivo é entrada padrão, abreviado como:
◦	STDIN.
▪	A entrada padrão, ou STDIN, é uma informação inserida normalmente pelo usuário pelo teclado.
▪	Quando um comando solicita dados ao shell, ele fornece ao usuário a capacidade de digitar comandos que, por sua vez, são enviados ao comando como STDIN.
•	O segundo descritor de arquivo é a saída padrão, abreviada como:
◦	STDOUT.
▪	Saída padrão, ou STDOUT, é a saída normal de comandos.
•	 Quando um comando funciona corretamente (sem erros), a saída produzida é chamada STDOUT.
•	Por padrão, STDOUT é exibido na janela do terminal em que o comando está sendo executado.
•	STDOUT também é conhecido como fluxo ou canal 1.
•	Podemos utilizar o caracter (>) para redirecionar, copiando o conteudo de um arquivo para dentro de outro.
•	O conteudo do arquivo sera substituido.
◦	Por exemplo:
▪	cat arquivo.txt> novo_arquivo.txt
•	Para acrescentar, em vez de substituir o conteúdo, a um arquivo, use um símbolo duplo maior que(>>):
•	O último descritor de arquivo é erro padrão, abreviado como:
◦	STDERR.
▪	Erro padrão, ou STDERR, são mensagens de erro geradas por comandos que não são executados corretamente..
•	Por padrão, STDERR é exibido na janela do terminal em que o comando está sendo executado.
•	STDERR também é conhecido como fluxo ou canal 2
•	O redirecionamento de E / S permite que o usuário redirecione STDIN para que os dados venham de um arquivo e STDOUT / STDERR para que a saída vá para um arquivo.
◦	O redirecionamento é obtido usando os caracteres de seta  < - >
▪	Por exemplo:
•	(echo "linha 1"> exemplo.txt)
◦	É importante saber que a seta única substitui qualquer conteúdo de um arquivo existente
◦	Também é possível preservar o conteúdo de um arquivo existente anexando-o.
▪	Use dois caracteres de seta ( >> ) para anexar a um arquivo em vez de substituí-lo:
•	Exemplo:
◦	(echo "outra linha">> exemplo.txt)
▪	Em vez de ser substituído, a saída do comando echo é adicionada à parte inferior do arquivo.
•	STDERR pode ser redirecionado da mesma forma que STDOUT.
◦	STDOUT e STDERR podem ser enviados para um arquivo usando o caractere E comercial (&) na frente do caractere de seta (>).
▪	 O conjunto de caracteres (&>) significa ambos 1>e 2>:
•	(ls /fake/etc/ppp &> all.txt)
•	Se você não deseja que STDERR e STDOUT vão para o mesmo arquivo, eles podem ser redirecionados para arquivos diferentes usando ambos > e 2>.
◦	Por exemplo:
▪	Para direcionar STDOUT para example.txt e STDERR para error.txt execute o seguinte comando:
•	(ls /fake/etc/ppp> exemplo.txt 2> error.txt)
◦	A ordem na qual os fluxos são especificados não importa.


SOBRE DIRETORIOS


/
Diretorio raiz
O diretorio raiz e o diretorio primario ou  mais alto diretorio em uma hierarquia de arquivos nos sistemas operacionais.
•	E oque contem todos os outros diretorios e arquivos do sistema.
◦	Pode ser comparado ao tronco de uma arvore invertida, de onde todos os ramos se originam.

/boot
Inicializacao.
O diretorio (/boot) contem os arquivos necessarios para inicializar o sistema.
•	Ou seja, processos de boot do Linux, quando o computador e ligado ficam em (/boot)
◦	Por exemplo:
▪	Os arquivos GRUB e seus kernels Linux são armazenados aqui.
•	As configuracoes do carregamento do boot não são encontrados neste diretorio, pois ficam armazenadas em (/etc) como outros arquivos de configuracao.
/initrd
Disco Ram inicial.
E um sistema de arquivos temporios usado pelo nucleo Linux durante o inicio do sistema.
•	E usado tipicamente para fazer os arranjos necessarios antes que o sistema de arquivos raiz possa ser montado.
◦	Usado quando esta criando um processo de bot initrd personalizado.

/etc
Configuracoes do sistema.
O diretorio (/etc) contem os arquivos de configuracao do sistema.
•	O diretorio (/etc), contem arquivos de todo o sistema de configuracao.
◦	Geralmente esses arquivos podem ser editados manualmente por um editor de texto.
•	Alem de  scripts especiais para iniciar ou interromper modulos e programas diversos.
•	E no diretorio (/etc) que se encontra;
◦	Por exemplo:
▪	O arquivo resolv.conf
•	Com uma relacao de servidores DNS que podem ser acessados pelo sistema
◦	Com os parametros necessarios para isso.

/sys
Arquivos de sistema e hardware.
Sistema de arquivos pseudo-virtual que fornece informacoes sobre o sistema e o hardware do computador.
•	Pode ser usado para alterar parametros do sistema e tambem para tarefas de debuggung.

/home
Arquivos pessoais
Diretorio inicial do usuario.
•	No diretorio (/home) ficam localizados os arquivos pessoais do usuario, tais como:
◦	Documentos, Fotografias
▪	Sempre dentro de pastas que levam o nome de cada usuario.
•	Tambem simbolizado pelo caracter til (~) que e equivalente a:
◦	(/home/usuario)
▪	Este é um diretório em que você tem acesso total e outros usuários por padrão, normalmente não têm acesso.
•	Quando o caminho fornecido como argumento para o comando (cd) começar com um caractere til (~), o terminal expandirá o caractere para o diretório inicial de um usuário com uma conta no sistema.
◦	Se nenhum outro caractere ou uma barra seguir o til, ele será expandido para o diretório inicial do usuário atualmente ativo no shell.
◦	Se um nome de usuário seguir imediatamente o caractere til, o shell expandirá o til e o nome do usuário para o diretório inicial desse nome de usuário.
▪	Por exemplo:
•	(sysadmin@localhost:/$ cd ~sysadmin)
◦	Seria expandido para:
▪	(/home/sysadmin).
•	Os caminhos que começam com um til são considerados caminhos absolutos, porque depois que o shell expande o caminho do til, um caminho absoluto é formado.
•	Vale lembrar que o diretorio pessoal do administrador do sistema não fica no mesmo local, e sim se localiza no diretorio (/root)

/root
Diretorio raiz do super usuario.
Diretorio home do usuario root, pronunciado como “eslash-ruut”.
•	Este diretorio não e a mesma coisa que a raiz do sistema (/), de onde descendem todos os diretorios do sistema.
•	Trata-se de um diretorio dedicado ao utilizador root.
◦	Na linha de comando, o utilizador root chega ao (/sbin) digitando (cd/root).



/bin
Binarios executaveis
Onde estao localizados os binarios executaveis que pode ser usado por qualquer usuario do sistema.
•	Sao comandos essenciais, usados para trabalhar com arquivos, textos e alguns recursos basicos de rede, tais como:
◦	cp, mv, ping e grep.

/sbin
Binarios do sistema.
Assim como o (/bin), esse diretorio armazena executaveis, mais com um diferencial:
•	Sao aplicativos utilizados por administradores de sistema com o proposito de realizar funcoes de manutencao e outras tarefas semelhantes.
•	Entre os comandos disponiveis estao:
◦	ifconfig
▪	Usado para configurar e controlar interfaces de rede TCP/IP.
◦	fdisk
▪	Permite particionar discos rigidos.

/usr
Programas diversos.
Se não for encontrado nos diretorios (/bin) ou (/sbin), ele certamente estara no (/usr).
•	O (/usr) reune executaveis, bibliotecas e ate documentacao de softwares usados pelos usuarios ou administradores de sistema.
◦	Alem disso, sempre que você compilar e instalar um programa a partir do codigo-fonte, ele sera instalado no diretorio (/usr).

/lib
Bibliotecas.
Neste diretorio do sistema de arquivos ficam localizadas as bibliotecas usadas pelos comandos presentes em (/bin) e (/sbin).
•	Normalmente, os arquivos de bibliotecas comecam com os prefixos:
◦	lb ou lib
▪	E possuem extensao so.

/opt
Pacotes opcionais.
Aplicativos adicionais, que não são essenciais para o sistema, são instalados neste diretorio.
•	Muito usado por determinados Software proprietarios que não obdecem ao FHS.

“Para acessar os arquivos de um CD, Pendrive ou Disco Rigido presente em outra maquida de rede, e necessario “MONTAR” esse conteudo no sistema de arquivos local, isso e, torna-lo acessivel como se fosse apenas mais um diretorio no sistema”.

/media
Midias.
Em  (/Media) ficam montadas todas as midias removiveis, como:
•	Dispositivos USB e DVD`s de dados.

/mnt
Ponto de montagens temporarios.
O diretorio (/mnt) fica reservado aos administradores que precisam montar temporariamente um sitema de arquivos externo.

/srv
Servicos.
Dados de servidores e servicoes que estao em execucao no computador ficam armazenados dentro deste diretorio.

“No Linux tudo e apresentado na forma de arquivos. Ao plugar um Pendrive no computador, por exemplo, um arquivo sera criado dentro do diretorio (/dev) e ele servira como interface para acessar ou gerenciar o drive USB.”

/dev
Arquivos de dispositivos.
Neste diretorio e encontrado caminhos semalhantes para acessar terminais e quaisquer dispositivos conectados ao computador, como:
•	Mouse e ate modens.

/var
Arquivos variaveis.
Todo arquivo que aumenta de tamanho ao longo do tempo esta localizado no diretorio de arquivos variaveis.
•	Um bom exemplo são os logs do sistema
◦	Ou seja, registros em forma de texto de atividades realizadas no Linux, como os logins feitos ao longo dos meses.


/proc
Processos do sistema.
Nesse diretorio são encontrados arquivos que revelam informacoes sobre os recursos e processos em execucao no sistema.
•	Por exemplo:
◦	Para saber ha quanto tempo o Linux esta sendo usado desde a ultima vez em que foi iniciado, basta ler o arquivo.
▪	(/proc/uptime).


/tmp
Arquivos temporarios.
Arquivos e diretorios criados temporariamente tanto pelo sistema quanto pelos usuarios devem ficar nesse diretorio.
•	Boa parte deles são apagados sempre que o computador e reiniciado.

/lost+found/
Perdidos e achados do sistema.
Este diretorio serve precisamente para oque seu nome indica, perdidos e achados.
•	Se por alguma razao o sistema crash  e for encerrado inesperadamente, da próxima vez  que o sistema for inicializado, ele sera verificado e todos os ficheiros ou fragmentos encontrados sera colocados no diretorio (/lost+found/).
◦	Este procedimento permite que os utilizadores consigam recuperar o maximo de informacoes possíveis após uma falha de sistema.

/run
Arquivos de aplicacoes.
Recentemente acrescentado aos sistemas de diretorios.
•	Neste diretorio ficam ficheiros com informacoes necessarias para que um determinado programa ou processo possa ser executado.
◦	Pode-se dizer  que e uma area de trabalho que os programas do sistema podem usar.

/selinux/
Seguranca reforcada no Linux.
Este sistema apenas esta incluso em algumas distribuicoes.
•	Selinux significa “Security Enhanced Linux”.
◦	Trata-se de um modulo de seguranca com diversas funcionalidades que permitem segurar um sistema Linux.
▪	Quando este modulo se encontra num sistema o diretorio (/selinux) pode ser criado, incluindo ficheiros associados ao funcionamento deste modulo, mas tambem  um sistema de ficheiro virtual.


SOBRE EDITORES DE TEXTO

vi
O editor de texto principal para Linux e UNIX é o vi.
•	O editor (vi) esta disponivel  em todas as distribuicoes Linux do mundo.
◦	Isso não e verdade para nenhum outro editor.
•	O editor (vi) pode ser executado em uma CLI (Interface da Linha de Comandos) e em uma GUI (Interface Grafica de Usuario).
•	A Maioria dos sistemas Linux não incluem o (vi) original, mais uma versao aprimorada conhecida como (vim).
•	Existem tres modos usados no vi:
◦	Modo de comando:
▪	O modo de comando e usado para digitar comandos, como aqueles usados para mover um documento, manipular textos e acessar os outros dois modos.
•	Para retornar ao modo de comando a qualquer momento, pressione a tecla ESC.
▪	Os comandos de movimento do (vi) tem dois aspectos:
•	Um movimento e um prefixo de numero opcional.
◦	Que indica quantas vezes repetir esse movimento
•	O formato geral e o seguinte:
◦	[contagem] movimento.
▪	A tabela a seguir resume as teclas de movimento disponiveis:
•	Movimento:		Resultado:
◦	h			Deixou um caracter
◦	j			Abaixo uma linha
◦	k			Ate uma linha
◦	l			Um personagem a direita
◦	w			Uma palavra para a frente
◦	b			Uma palavra de volta
◦	^			Inicio da linha
◦	$			Fim da linha.
•	Desde a atualizacao (vim), tambem e possível usar as teclas de seta em vez de h, j, k ,l respectivamente.
▪	Acoes do modo de comando.
•	A convensao padara para editar conteudo com processadores de texto e usar copiar, recortar e colar.
◦	O programa (vi) não possui nenhum desses.
▪	Em vez disso, o (vi) usa os tres comandos a seguir:
•	Padrao	:		vi:		Significado:
◦	Cortar			d		Excluir
◦	Copiar			y		Puxão
◦	Colar			P|p		Colocar
▪	Comandos uteis do editor vi
			Comando		Descrição
•	Ctrl + W		Procure o documento
•	Ctrl + W e , em seguida, Control + R	pesquisar e substituir
•	Ctrl + G		Mostra todos os comandos possíveis
•	Ctrl + Y / V		Página para cima / baixo
•	Ctrl + C		Mostra a posição atual no arquivo e o tamanho do arquivo

◦	Modo de insercao:
▪	O modo de insercao e usado para adicionar texto ao documento.
•	Existem algumas maneiras de entrar no modo de insercao do modo de comando, cada uma idierenciada por onde a insercao de texto comecara.
◦	Modo de ex:
◦	Originalmente , o editor (vi) era chamado de editor (ex).
▪	O nome vi era a abreviacao de visual do comando no editor (ex), que mudou o editor para o modo “visual”.

SOBRE ARQUIVOS E DIRETORIOS ESPECIAIS

Setuid

Quando a permissão setuid é definida em um arquivo binário executável (um programa), o arquivo binário é executado como o proprietário do arquivo, não como o usuário que o executou.
 Essa permissão é definida em um punhado de utilitários do sistema para que possam ser executados por usuários normais, mas executados com as permissões de root, fornecendo acesso aos arquivos do sistema aos quais o usuário normal normalmente não tem acesso.

As permissões /etc/shadowativadas não permitem que usuários normais vejam (ou modifiquem) o arquivo. Como o arquivo pertence ao rootusuário, o administrador pode modificar temporariamente as permissões para visualizar ou modificar este arquivo.

O passwdcomando tem a permissão setuid especial definida. Quando o passwdcomando é executado e acessa o /etc/shadowarquivo, o sistema age como se o usuário que está acessando o arquivo seja o proprietário do passwdcomando (o usuário root), não o usuário que está executando o comando.

Observe a saída do lscomando acima; a permissão setuid é representada pelo snas permissões do proprietário, onde a permissão de execução normalmente seria representada. Uma minúscula ssignifica que as permissões setuid e de execução estão definidas, enquanto uma maiúscula Ssignifica que apenas setuid e não a permissão de execução do usuário está definida.

Como as permissões de leitura, gravação e execução, as permissões especiais podem ser definidas com o chmodcomando, usando os métodos simbólico e octal.

Para adicionar a permissão setuid simbolicamente, execute:

arquivo chmod u + s
Para adicionar a permissão setuid numericamente, adicione 4000 às permissões existentes do arquivo (suponha que o arquivo originalmente tinha 775 para sua permissão no exemplo a seguir):

arquivo chmod 4775
Para remover a permissão setuid simbolicamente, execute:

arquivo chmod us
Para remover a permissão setuid numericamente, subtraia 4000 das permissões existentes do arquivo:

arquivo chmod 0775


Setgid

A permissão setgid é semelhante à setuid, mas faz uso das permissões de proprietário do grupo. Existem duas formas de permissões setgid: setgid em um arquivo e setgid em um diretório. O comportamento de setgid depende se ele está definido em um arquivo ou diretório.


A permissão setgid em um arquivo é muito semelhante a setuid; ele permite que um usuário execute um arquivo binário executável de uma maneira que forneça acesso de grupo adicional (temporário). O sistema permite que o usuário que executa o comando pertença efetivamente ao grupo que possui o arquivo, mas apenas no programa setgid.

Use a seguinte sintaxe para adicionar a permissão setgid simbolicamente:

chmod g + s < arquivo | diretório >
Para adicionar a permissão setgid numericamente, adicione 2.000 às permissões existentes do arquivo (suponha no exemplo a seguir que o diretório originalmente tinha 775 para suas permissões):

chmod 2775 < arquivo | diretório >
Para remover a permissão setgid simbolicamente, execute:

chmod gs < arquivo | diretório >
Para remover a permissão setgid numericamente, subtraia 2.000 das permissões existentes do arquivo:

chmod 0775 < arquivo | diretório >

Sticky Bit

A permissão sticky bit é usada para evitar que outros usuários excluam arquivos que não são de sua propriedade em um diretório compartilhado. Lembre-se de que qualquer usuário com permissão de gravação em um diretório pode criar arquivos nesse diretório, bem como excluir qualquer arquivo do diretório, mesmo que não seja o proprietário do arquivo!

Uma minúscula tsignifica que tanto o sticky bit quanto as permissões de execução estão definidas para outros. Uma maiúscula Tsignifica que apenas a permissão sticky bit está definida.

Enquanto a capital Sindica um problema com as permissões setuid ou setgid, uma capital Tnão indica necessariamente um problema, desde que o proprietário do grupo ainda tenha a permissão de execução.

Para definir a permissão do bit sticky simbolicamente, execute um comando como o seguinte:

chmod o + t < diretório >
Para definir a permissão do bit sticky numericamente, adicione 1000 às permissões existentes do diretório (suponha que o diretório no exemplo a seguir tinha originalmente 775 para suas permissões):

chmod 1775 < arquivo | diretório >
Para remover a permissão sticky simbolicamente, execute:

chmod ot < diretório >
Próximo Próximo Para remover a permissão sticky bit numericamente, subtraia 1000 das permissões existentes do diretório:

chmod 0775 < diretório >

Links

Você pode criar um arquivo vinculado àquele que está profundamente enterrado. Esse novo arquivo pode ser colocado no diretório inicial ou em qualquer outro local conveniente. Quando você acessa o arquivo vinculado, ele acessa o conteúdo do valuable-information.txtarquivo.

Cada método de vinculação, físico e simbólico, resulta no mesmo acesso geral, mas usa técnicas diferentes. Existem prós e contras em cada método, portanto, é importante saber as duas técnicas e quando usá-las.

Para entender os links físicos , é útil entender um pouco sobre como o sistema de arquivos controla os arquivos. Para cada arquivo criado, há um bloco de dados no sistema de arquivos que armazena os metadados do arquivo. Metadados incluem informações sobre o arquivo, como permissões, propriedade e carimbos de data / hora. Os metadados não incluem o nome ou o conteúdo do arquivo, mas incluem todas as outras informações sobre o arquivo.

Esses metadados são chamados de tabela de inode do arquivo . A tabela inode também inclui ponteiros para os outros blocos no sistema de arquivos chamados blocos de dados, onde os dados são armazenados.

Cada arquivo em uma partição possui um número de identificação exclusivo denominado número de inode . O ls -icomando exibe o número de inode de um arquivo.

Como usuários e grupos, o que define um arquivo não é seu nome, mas sim o número ao qual foi atribuído. A tabela de inode não inclui o nome do arquivo. Para cada arquivo, há também uma entrada que é armazenada em uma área de dados do diretório (bloco de dados) que inclui uma associação entre um número de inode e um nome de arquivo.

No bloco de dados para o /etcdiretório, haveria uma lista de todos os arquivos neste diretório e seu número de inode correspondente. Por exemplo:

Nome do arquivo	Número Inode
passwd	123
shadow	175
group	144
gshadow	897

Quando você tenta acessar o /etc/passwdarquivo, o sistema usa esta tabela para traduzir o nome do arquivo em um número de inode. Em seguida, ele recupera os dados do arquivo observando as informações na tabela de inode do arquivo.

Links físicos são dois nomes de arquivo que apontam para o mesmo inode. Por exemplo, considere as seguintes entradas de diretório:

Nome do arquivo	Número Inode
passwd	123
mypasswd	123
shadow	175
group	144
gshadow	897

O número de contagem de links indica quantos links físicos foram criados. Quando o número tem o valor um, o arquivo tem apenas um nome vinculado ao inode.

Para criar links físicos, o lncomando é usado com dois argumentos. O primeiro argumento é um nome de arquivo existente para vincular, chamado de destino, e o segundo argumento é o novo nome de arquivo para vincular ao destino

Quando o lncomando é usado para criar um link físico, o número de contagem do link aumenta em um para cada nome de arquivo adicional:

Um link simbólico , também chamado de soft link , é simplesmente um arquivo que aponta para outro arquivo. Já existem vários links simbólicos no sistema, incluindo vários no /etcdiretório:

Para criar um link simbólico, use a -sopção com o lncomando:


Vantagem: os links físicos não têm um único ponto de falha.

Um dos benefícios de usar links físicos é que cada nome de arquivo para o conteúdo do arquivo é equivalente. Se você tiver cinco arquivos vinculados fisicamente, a exclusão de quaisquer quatro desses arquivos não resultará na exclusão do conteúdo real do arquivo.

Links simbólicos, entretanto, têm um único ponto de falha: o arquivo original. Considere o seguinte exemplo no qual o acesso aos dados falha se o arquivo original for excluído. O mytest.txtarquivo é um link simbólico para o text.txtarquivo:

Se o arquivo original test.txtfor removido, todos os arquivos vinculados a ele, incluindo o mytest.txtarquivo, falharão:

Vantagem: os links virtuais são mais fáceis de ver.

Às vezes, pode ser difícil saber onde existem os links físicos para um arquivo. Se você vir um arquivo normal com uma contagem de links maior que um, você pode usar o findcomando com os -inumcritérios de pesquisa para localizar os outros arquivos que têm o mesmo número de inode. Para encontrar o número do inode, você primeiro usaria o ls -icomando:

Vantagem: Os links de software podem ser vinculados a qualquer arquivo.

Como cada sistema de arquivos (partição) tem um conjunto separado de inodes, não podem ser criados links físicos que tentem cruzar os sistemas de arquivos:



Vantagem: Os links simbólicos podem ser vinculados a um diretório.

Outra limitação dos links físicos é que eles não podem ser criados em diretórios. O motivo dessa limitação é que o próprio sistema operacional usa links físicos para definir a hierarquia da estrutura de diretório. O exemplo a seguir mostra a mensagem de erro exibida se você tentar um link físico para um diretório:

SOBRE SHELL SCRIPT BASICO


Um script de shell é um arquivo de comandos executáveis que foram armazenados em um arquivo de texto.
•	Quando o arquivo é executado, cada comando é executado.
•	A execução de um script pode ser feita passando-o como argumento para o seu shell ou executando-o diretamente:
◦	Exemplo
▪	sh exemplo.sh
•	 ./exemplo.sh
•	É raro ter o diretório atual no caminho de pesquisa binária $PATH, portanto o nome é prefixado (./) para indicar que ele deve ficar sem o diretório atual.
•	O erro Permission denied significa que o script não foi marcado como executável.
◦	chmod é usado para alterar as permissões de um arquivo.
•	Existem vários shells com sua própria sintaxe de idioma.
•	Portanto, scripts mais complicados indicarão um shell específico, especificando o caminho absoluto para o intérprete como a primeira linha, prefixada (#!).
◦	exemplo:
▪	#! /bin/sh
•	echo "Olá, mundo!"
ou
▪	#! /bin/bash
•	echo "Olá, mundo!"
•	Os dois personagens (#!) são tradicionalmente chamados de hash e bang, respectivamente, o que leva à forma abreviada de "shebang" quando usados no início de um script.
◦	Aliás, o shebang (ou crunchbang) é usado para scripts de shell tradicionais e outras linguagens baseadas em texto como Perl, Ruby e Python.
•	Além de executar comandos, existem três tópicos com os quais você deve se familiarizar:
◦	Variáveis:
▪	 Que contêm informações temporárias no script
◦	Condicionais:
▪	Que permitem fazer coisas diferentes com base nos testes que você escreve
◦	Loops:
▪	Que permitem fazer a mesma coisa repetidamente
•	Variaveis:
◦	Variáveis são uma parte essencial de qualquer linguagem de programação.
▪	Um uso muito simples de variáveis é mostrado aqui:
•	#! / bin / bash
•	ANIMAL = "pinguim"
•	echo "Meu animal favorito é um $ANIMAL"
▪	Em seguida, o script faz echo de uma sequência no console.
▪	A sequência contém o nome da variável precedida por um cifrão.
▪	Quando o intérprete vê esse cifrão, reconhece que estará substituindo o conteúdo da variável, chamada interpolação.
▪	A saída do script é então My favorite animal is a penguin
▪	Então lembre-se do seguinte:
•	Para atribuir a uma variável, basta usar o nome da variável.
Para acessar o conteúdo da variável, prefixe-a com um cifrão.
▪	Aqui, mostramos uma variável sendo atribuída ao conteúdo de outra variável
•	#! / bin / bash
•	ANIMAL = pinguim
•	ALGO = $ ANIMAL
•	echo "Meu animal favorito é $ ALGO"
▪	Outra maneira de atribuir a uma variável é usar a saída de outro comando como o conteúdo da variável, colocando o comando em back ticks:
•	#! / bin / bash
•	CURRENT_DIRECTORY = `pwd`
•	echo "Você está em $ CURRENT_DIRECTORY"
▪	Esse padrão é frequentemente usado para processar texto.
▪	Você pode pegar o texto de uma variável ou arquivo de entrada e passá-lo através de outro comando como “sed” ou “awk” para extrair determinadas partes e manter o resultado em uma variável.
•	Sed
◦	Usado para editar fluxos (STDIN)
•	awk
◦	Usado para scripts
▪	É possível obter a entrada do usuário do seu script e atribuí-la a uma variável através do comando read:
•	O comando (read) pode aceitar uma sequência diretamente do teclado ou como parte do redirecionamento de comando.
▪	Existem algumas variávei especiais além das que você definiu.
▪	Você pode passar argumentos para o seu script:
•	#! / bin / bash
•	eco "Olá $ 1"
▪	Um cifrão $ seguido de um número N corresponde ao argumento N enésimo passado ao script.
▪	Depois que um programa é executado, seja um binário ou um script, ele retorna um código de saída que é um número inteiro entre 0 e 255.
▪	Você pode testar isso através da variável ($?) para ver se o comando anterior foi concluído com êxito.
•	Exemplo:
◦	grep -q root / etc / passwd
◦	echo $?
◦	grep -q slartibartfast / etc / passwd
◦	echo $?
▪	O comando (grep) foi usado para procurar uma sequência dentro de um arquivo com a bandeira (–q), o que significa "silencioso".
▪	O (grep), enquanto estiver executando no modo silencioso, retorna 0 se a sequência foi encontrada e 1 se não.
▪	Essas informações podem ser usadas condicionalmente para executar uma ação com base na saída de outro comando.
▪	Da mesma forma, você pode definir o código de saída do seu próprio script com o comando exit:
▪	Por convenção, um código de saída 0 significa "está tudo bem".
▪	Qualquer código de saída maior que a média 0 ocorreu algum tipo de erro, específico do programa.
▪	Acima você viu que os usos de (grep) 1 para significar a cadeia não foi encontrado.
•	Condicionais:
◦	Agora que você pode olhar e definir variáveis, é hora de fazer seu script executar funções diferentes com base em testes, chamados ramificação.
◦	A instrução if é o operador básico para implementar a ramificação.
◦	Uma declaração if básica é assim:
▪	if algum comando; then
▪	# fazer isso se alguma_coisa tem um codigo de saida 0
▪	fi
◦	O próximo exemplo executará "algum comando" (na verdade, tudo até o ponto-e-vírgula) e se o código de saída for 0 o conteúdo até o fechamento fiserá executado.
◦	Usando o que você conhece de grep, agora você pode escrever um script que faça coisas diferentes com base na presença de uma sequência no arquivo de senha:
▪	#! / bin / bash
▪	if grep -q root / etc / passwd; then
•	raiz do echo está no arquivo de senhas,
▪	eles
•	raiz do eco está ausente no arquivo de senhas
▪	fi
◦	Nos exemplos anteriores, você deve se lembrar que o código de saída (grep) é 0 se a sequência for encontrada.
◦	O comando (test) fornece acesso fácil aos operadores de comparação e teste de arquivo.
▪	Por exemplo:
•	Comando			Descrição
◦	test –f /dev/ttyS0		0 se o arquivo existir
◦	test ! –f /dev/ttyS0		0 se o arquivo não existir
◦	test –d /tmp			0 se o diretório existir
◦	test –x `which ls`		substituir a localização ls, em seguida, test se o usuário pode executar
◦	test 1 –eq 1			0 se a comparação numérica for bem-sucedida
◦	test ! 1 –eq 1	NOT – 	0 se a comparação falhar
◦	test 1 –ne 1			Mais fácil, test para desigualdade numérica
◦	test “a” = “a”			0 se a comparação de string for bem-sucedida
◦	test “a” != “a”			0 se as cordas são diferentes
◦	test 1 –eq 1 –o 2 –eq 2	-o é OR: pode ser o mesmo
◦	test 1 –eq 1 –a 2 –eq 2	-a é AND: ambos devem ser iguais
◦	É importante notar que as comparações test de números inteiros e seqüências de caracteres diferem.
◦	01 e 1 são iguais por comparação numérica, mas não por comparação de cadeias.
◦	Você deve sempre ter cuidado para lembrar que tipo de entrada espera.
◦	Existem muitos outros testes, como (–gt) para maior que, maneiras de testar se um arquivo é mais novo que o outro e muitos mais.
◦	Test é bastante detalhado para um comando que é usado com tanta frequência; portanto, existe um apelido para ele [(colchete esquerdo).
◦	Se você colocar suas condições entre colchetes, é o mesmo que correr test.
◦	Portanto, essas declarações são idênticas.
▪	if teste –f / tmp / foo; then
▪	if [-f / tmp / foo]; then
◦	A declaração if tem um formato final que permite fazer várias comparações ao mesmo tempo usando elif(abreviação de else if).
▪	#! / bin / bash
▪	if ["$ 1" = "olá"]; então
▪	echo "olá você mesmo"
▪	elif ["$ 1" = "adeus"]; então
▪	echo "prazer em conhecê-lo"
▪	echo "Espero vê-lo novamente"
▪	else
▪	echo "Eu não entendi isso"
▪	fi
◦	Os testes if/ elif/ else podem se tornar bastante detalhados e complicados.\
◦	A declaração case fornece uma maneira diferente de facilitar vários testes.
▪	#! / bin / bash
▪	case "$ 1" em
▪	hello | hi)
▪	echo "olá você mesmo"
▪	;;
▪	adeus)
▪	echo "prazer em conhecê-lo"
▪	echo "Espero vê-lo novamente"
▪	;;
▪	*)
▪	echo "eu não entendi isso"
▪	esac
◦	A declaração case começa com uma descrição da expressão que está sendo testado:
◦	A expressão aqui é a citada .case EXPRESSION in
◦	O exemplo anterior primeiro procura por hellou hi; várias opções são separadas pela barra vertical, |que é um operador OR em muitas linguagens de programação.
•	Loops:
◦	Os loops permitem que o código seja executado repetidamente.
◦	Eles podem ser úteis em várias situações, como quando você deseja executar os mesmos comandos sobre cada arquivo em um diretório ou repetir alguma ação 100 vezes.
◦	Existem dois loops principais nos scripts de shell:
▪	o forloop e o whileloop.
◦	for loops são usados quando você tem uma coleção finita sobre a qual deseja iterar, como uma lista de arquivos ou uma lista de nomes de servidores:
▪	#! / bin / bash
▪	SERVERS = "servera serverb serverc"
▪	for S in $SERVERS; do
▪	echo "Fazer algo para US $S"
▪	done
◦	A lista não precisa ser uma variável.
◦	Este exemplo mostra mais duas maneiras de passar uma lista.
▪	#! / bin / bash
▪	for NAME in Sean Jon Isaac David; do
▪	echo "Hello $NAME"
▪	done
▪	for S in *; fazer
▪	echo "Fazer algo para US $S"
▪	done
◦	O outro tipo de loop, um whileloop, opera em uma lista de tamanho desconhecido, seu trabalho é continuar executando e, em cada iteração, execute a test para verificar se deve executar outra hora.
◦	Você pode pensar nisso como "enquanto alguma condição é verdadeira, faça as coisas".
▪	#! / bin / bash
▪	i = 0
▪	while [$i -lt 10]; do
▪	echo $i
▪	i = $ (($i + 1))
▪	done
▪	echo “contagem Done”
◦	Dentro do whileloop, o valor atual de i é ecoado e depois 1 é adicionado a ele através do comando e atribuído novamente .
◦	Depois de 10, a instrução retorna false e o processamento continua após o “loop.$(( arithmetic ))iiwhile”.


SOBRE HARDWARE BASICO DE UM COMPUTADOR

PLACA MAE
A placa-mãe ou placa de sistema é a principal placa de hardware do computador através da qual a unidade central de processamento CPU, a memória de acesso aleatório RAM e outros componentes estão todos conectados.
•	Dependendo do tipo de computador (laptop, desktop, servidor), alguns dispositivos, como processadores e RAM, são conectados diretamente à placa-mãe, enquanto outros, como placas de expansão, são conectados por um barramento.
•	A placa do sistema de muitos computadores contém o que é conhecido como BIOS ou um sistema básico de entrada e saída.
•	O System Management BIOS, ou SMBIOS, é um padrão que define as estruturas de dados e como comunicar informações sobre o hardware do computador.

PROCESSADORES
Uma unidade central de processamento (CPU ou processador) é um dos componentes de hardware mais críticos de um computador.
•	O processador é o cérebro do computador, onde a execução do código ocorre e onde a maioria dos cálculos é feita.
•	Ele é conectado diretamente (soldado) à placa-mãe, pois as placas-mãe geralmente são configuradas para trabalhar com tipos específicos de processadores.
•	Se um sistema de hardware tiver mais de um processador, o sistema será chamado de multiprocessador.
◦	Se mais de um processador for combinado em um único chip de processador geral, ele será chamado de vários núcleos.
•	Embora o suporte esteja disponível para mais tipos de processadores no Linux do que qualquer outro sistema operacional, existem basicamente apenas dois tipos de processadores usados em computadores de mesa e servidores: x86 e x86_64 .
◦	Em um sistema x86, o sistema processa os dados 32 bits por vez;
◦	em um x86_64, o sistema processa dados de 64 bits por vez.
▪	Um sistema x86_64 também é capaz de processar dados de 32 bits por vez em um modo compatível com versões anteriores.
▪	Uma das principais vantagens de um sistema de 64 bits é a capacidade de trabalhar com mais memória, enquanto outras vantagens incluem maior eficiência do processamento e maior segurança.
•	A Intel originou a família de processadores x86 em 1978 com o lançamento do processador 8086.
•	Desde então, a Intel produziu muitos outros processadores que são aprimoramentos para o 8086 original; eles são conhecidos genericamente como processadores x86.
•	Esses processadores incluem os modelos 80386 (i386), 80486 (i486), Pentium (i586) e Pentium Pro (i686).
•	Além da Intel, outras empresas, como AMD e Cyrix, também produziram processadores compatíveis com x86.
◦	Embora o Linux seja capaz de dar suporte aos processadores da geração i386, muitas distribuições (especialmente as que oferecem suporte corporativo, como SUSE, Red Hat e Canonical) limitam seu suporte ao i686 ou posterior.
•	A família de processadores x86_64, incluindo os de 64 bits da Intel e AMD, está em produção desde o ano 2000.
•	Como resultado, quase todos os processadores modernos hoje vendidos são do tipo x86_64.
•	Embora o hardware esteja disponível há mais de uma década, o software para suportar essa família de processadores tem sido muito mais lento para se desenvolver.
•	Para ver a qual família a CPU do sistema atual pertence, use o comando (arch).
◦	sysadmin@localhost:~$ arch
•	Para mais informações sobre a CPU, use o comando (lscpu):
◦	sysadmin@localhost:~$ lscpu
•	Use o comando head com a opção (-n) para listar as primeiras 20 linhas do arquivo cpuinfo:
•	Ser capaz de exibir informações da CPU pode ser importante ao tentar determinar se recursos mais avançados do Linux podem ser usados em seu sistema.
•	Para obter mais detalhes sobre sua (s) CPU (s), você pode examinar o arquivo /proc/cpuinfo, especialmente os "sinalizadores" listados que determinam se sua CPU possui ou não determinados recursos.
•	Sinalizadores:
◦	fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdt scp lm constant_tsc arch_perfmon pqs bts xp ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdc m pcid dca sse4_1 sse4_2 popcnt aes lahf_lm tpr_shadow vnmi flexprioridade ept vpi dtherm ida arat

MEMORIA DE ACESSO ALEATORIO (RAM)
A placa-mãe normalmente possui slots nos quais a memória de acesso aleatório (RAM) pode ser conectada ao sistema.
•	Os sistemas de arquitetura de 32 bits podem usar até 4 gigabytes (GB) de RAM, enquanto as arquiteturas de 64 bits são capazes de endereçar e usar muito mais RAM.
•	Em alguns casos, a RAM de um sistema pode não ser suficiente para lidar com todos os requisitos do sistema operacional.
•	Uma vez chamados, os programas são carregados na RAM, juntamente com os dados que precisam armazenar, enquanto as instruções são enviadas ao processador quando elas são executadas.
•	Quando o sistema está com pouca memória RAM, a memória virtualizada chamada espaço de troca é usada para armazenar temporariamente os dados no disco.
•	Os dados armazenados na RAM que não foram utilizados recentemente são movidos para a seção do disco rígido designada como swap, liberando mais RAM para uso dos programas atualmente ativos.
•	Se necessário, esses dados trocados podem ser movidos novamente para a RAM posteriormente.
•	O sistema faz tudo isso automaticamente desde que a troca esteja configurada
•	Para visualizar a quantidade de RAM no seu sistema, incluindo o espaço de troca, execute o comando  (free).
•	A saída mostra a quantidade de memória em megabytes quando a opção (-m ) é usada
◦	free -m
•	E em gigabytes quando a opção (-g) é usada:
◦	free -g
◦	O comando free tem uma opção -m para forçar a saída a ser arredondada para o megabyte mais próximo (MB).
◦	E uma opção -g para forçar a saída a ser arredondada para o gigabyte mais próximo (GB):
◦	Grande parte da RAM física é livre e, portanto, não é necessário que a RAM virtual (espaço de troca) seja usada no momento.
•	No caso de falta de memória, a troca é usada.
◦	Swap é o espaço no disco rígido usado para armazenar temporariamente os dados que deveriam ser armazenados na RAM.

BUSES
Um barramento é uma conexão de alta velocidade que permite a comunicação entre computadores ou os componentes dentro de um computador.
•	A placa-mãe possui barramentos que permitem a conexão de vários dispositivos com o sistema, incluindo o PCI (Peripheral Component Interconnect) e o Universal Serial Bus (USB) .
•	A placa-mãe também possui conectores para monitores, teclados e mouses.
•	Para que o hardware funcione, o kernel do Linux normalmente carrega um driver ou módulo.
◦	Use o comando lsmod para visualizar os módulos carregados no momento:

DISPOSITIVOS PERIFERICOS
Dispositivos periféricos são componentes conectados a um computador que permitem armazenamento de entrada, saída ou dados.
•	Teclados, mouses, monitores, impressoras e discos rígidos são considerados periféricos e são acessados pelo sistema para executar funções fora do processamento central.
•	Para visualizar todos os dispositivos conectados pelo barramento PCI, o usuário pode executar o comando (lspci).
◦	Use o comando lspci com a opção -k para mostrar dispositivos junto com o driver do kernel e os módulos usados:
▪	lspci -k

DISPOSITIVO DE BARRAMENTO SERIAL UNIVERSAL
Enquanto o barramento PCI é usado para muitos dispositivos internos, como placas de som e de rede, um número cada vez maior de dispositivos externos (ou periféricos) é conectado ao computador via USB.
•	Os dispositivos conectados internamente geralmente são plugados a frio , o que significa que o sistema deve ser desligado para conectar ou desconectar um dispositivo. Os dispositivos USB são hot-plug , o que significa que podem ser conectados ou desconectados enquanto o sistema estiver em execução.
•	Embora os dispositivos USB sejam hot-plug por design, é importante garantir que todos os sistemas de arquivos montados sejam desmontados corretamente, ou perda de dados e corrupção do sistema de arquivos podem ocorrer.
•	Para exibir os dispositivos conectados ao sistema via USB, execute o comando (lsusb):
•	Os discos rígidos , também chamados de discos rígidos, dispositivos de disco ou dispositivos de armazenamento, podem ser conectados ao sistema de várias maneiras; o controlador pode ser integrado à placa-mãe, em uma placa PCI ou como um dispositivo USB.
•	Para os propósitos da maioria dos sistemas Linux, um disco rígido geralmente pode ser definido como qualquer dispositivo de armazenamento eletromecânico ou eletrônico que contém dados a serem acessado pelo sistema.
•	Os discos rígidos são divididos em uma ou mais partições .
◦	Uma partição é uma divisão lógica de um disco rígido, projetada para ocupar uma grande quantidade de espaço de armazenamento disponível e dividi-lo em áreas menores.
◦	Embora seja comum no Microsoft Windows ter uma única partição para cada disco rígido, nas distribuições Linux, são comuns várias partições por disco rígido.
•	Alguns discos rígidos usam uma tecnologia de particionamento chamada MBR (Master Boot Record), enquanto outros usam um tipo de particionamento chamado Guid Partitioning Table (GPT) .
•	O tipo de particionamento MBR tem sido usado desde os primeiros dias do computador pessoal (PC) e o tipo GPT está disponível desde o ano 2000.
•	Um termo antigo usado para descrever um disco rígido interno é “disco fixo” , pois o disco é fixo (não removível).
◦	Este termo deu origem a vários nomes de comandos:
◦	fdisk, cfdiske sfdisk, que são ferramentas para trabalhar com o MBR particionando discos.
•	Os discos GPT usam um tipo mais recente de particionamento, que permite ao usuário dividir o disco em mais partições do que o MBR suportaria.
•	O GPT também permite ter partições que podem ser maiores que dois terabytes (o MBR não).
•	As ferramentas para  gestão  dos discos GPT são nomeadas de forma semelhante aos seus homólogos:
◦	fdisk gdisk, cgdisk, e sgdisk.
•	Há também uma família de ferramentas que tentam oferecer suporte aos discos do tipo MBR e GPT.
•	Este conjunto de ferramentas inclui o comando parted e a  ferramenta gráfica gparted .
◦	Nota : Muitas distribuições Linux usam a ferramenta gparted na rotina de instalação, pois fornece uma interface gráfica para as poderosas opções disponíveis para criar novas partições, redimensionar as existentes (como partições do Windows) e muitas outras tarefas avançadas.
•	Os discos rígidos estão associados a nomes de arquivos (chamados de arquivos de dispositivo) armazenados no diretório /dev.
•	Cada nome de arquivo do dispositivo é composto de várias partes.
•	Tipo de arquivo
◦	O nome do arquivo é prefixado com base nos diferentes tipos de discos rígidos.
◦	Os discos rígidos IDE (Intelligent Drive Electronics ) começam com hd, enquanto os discos USB, SATA (Serial Advanced Technology Attachment) e SCSI (Small Computer System Interface) começam com sd.
•	Ordem do dispositivo
◦	Cada disco rígido recebe uma letra que segue o prefixo.
▪	Por exemplo, o primeiro disco rígido IDE seria nomeado
•	/dev/hda e o segundo seria /dev/hdb, e assim por diante.
•	Partição
◦	Finalmente, cada partição em um disco recebe um indicador numérico único.
◦	Por exemplo, se um disco rígido USB tiver duas partições, elas poderão ser associadas aos arquivos dispositivos /dev/sda1 e do /dev/sda2.
•	O exemplo a seguir mostra um sistema que tem três dispositivos sd:
◦	/dev/sda, /dev/sdbe /dev/sdc.
◦	 Além disso, há duas partições no primeiro dispositivo, como evidenciado pelos arquivos
▪	/dev/sda1 e /dev/sda2, e uma partição no segundo dispositivo, como evidenciado pelo arquivo:
•	/dev/sdb1:
•	Exemplo:
◦	root @ localhost : ~ $ ls / dev / sd *
▪	/ dev / sda / dev / sda1 / dev / sda2 / dev / sdb / dev / sdb1 / dev / sdc
•	O comando fdisk pode ser usado para exibir mais informações sobre as partições
•	O comando  fdisk é útil para identificar e manipular recursos de armazenamento em disco em um sistema.
•	Como pode ser usado para criar, formatar e excluir partições, além de obter informações, deve ser usado com cuidado no modo administrador para evitar a perda de dados.
•	O comando fdisk pode ser usado de duas maneiras: interativa e não interativa.
◦	Quando a opção (-l) é usada o comando fdisk, listará de maneira não interativa os dispositivos de bloco, o que inclui discos (discos rígidos) e volumes lógicos.
◦	Sem a opção (-l), o comando fdisk entra em um modo interativo que normalmente é usado para modificar partições em um dispositivo de disco.
◦	A opção  (-l) lista as tabelas de partição para os dispositivos especificados e sai
◦	Se nenhum dispositivo for fornecido, os mencionados em /proc/partitions (se esse arquivo existir) serão usados:
•	Particionamentos validos
◦	MBR
◦	GPT


DISCOS DE ESTADO SOLIDO
Embora a frase disco rígido seja normalmente considerada como abrangendo dispositivos de disco rotativo tradicionais, também pode se referir a unidades ou discos de estado sólido mais novos e muito diferentes.
•	Os discos de estado sólido são, basicamente, pen drives USB de maior capacidade na construção e na função.
•	Como não há partes móveis nem discos giratórios, apenas os locais de memória a serem lidos pelo controlador, um disco de estado sólido é mensurável e visivelmente mais rápido no acesso às informações armazenadas em seus chips de memória.
•	As vantagens de um disco de estado sólido incluem menor uso de energia, economia de tempo na inicialização do sistema, cargas de programa mais rápidas e menos calor e vibração sem partes móveis.
•	As desvantagens incluem custos mais altos em comparação com discos rígidos giratórios, menor capacidade devido ao custo mais alto e, se soldados diretamente na placa-mãe, onde não tem nenhuma capacidade de atualização trocando a unidade.

DRIVES OPTICOS
As unidades ópticas , geralmente denominadas CD-ROMs, DVDs ou Blu-Ray, são mídias de armazenamento removíveis.
•	Enquanto alguns dispositivos usados com discos ópticos são somente leitura, outros são capazes de gravar (gravar em) discos ao usar um tipo de disco gravável.
•	Existem vários padrões para discos graváveis e regraváveis, como CD-R, CD + R, DVD + RW e DVD-RW.
•	O local em que esses discos removíveis são montados no sistema de arquivos é uma consideração importante para um administrador do Linux.
•	As distribuições modernas geralmente montam os discos no diretorio /media, enquanto as distribuições mais antigas geralmente os montam no diretorio /mnt.
•	Por exemplo:
◦	Um pen drive USB pode ser montado no caminho /media/usbthumb.
•	Na montagem, a maioria das interfaces GUI solicita que o usuário execute alguma ação, como abrir o conteúdo do disco em um navegador de arquivos ou iniciar um programa de mídia.
•	Quando o usuário terminar de usar o disco, é necessário desmontá-lo usando um menu ou o comando umount.

DISPOSITIVOS DE EXIBICAO DE VIDEO
Existem três tipos de cabos de vídeo comumente usados: o cabo VGA (Video Graphics Array) analógico de 15 pinos mais antigo, mas ainda usado , a interface Digital Visual Interface (DVI) de 29 pinos mais recente e a interface multimídia de alta definição muito usada (HDMI), que suporta resoluções de até 4K ou Ultra HD.
•	Para que os monitores funcionem corretamente com dispositivos de exibição de vídeo, eles devem ser capazes de suportar a mesma resolução que o dispositivo de exibição de vídeo.
•	Normalmente, o software que aciona o dispositivo de exibição de vídeo pode detectar automaticamente a resolução máxima que a tela e o monitor podem suportar e definir a resolução da tela para esse valor.

FONTES DE ALIMENTACAO
As fontes de alimentação são os dispositivos que convertem corrente alternada (120v, 240v) em corrente contínua, que o computador usa em várias tensões (3,3v, 5v, 12v).
•	Fontes de alimentação geralmente não são programáveis; no entanto, sua função adequada tem um grande impacto no restante do sistema.

SOBRE PROCESSOS DO SISTEMA
O diretório /proc parece ser um diretório comum, como /usr ou /etc, mas não é.
•	Diferente dos diretórios /usr ou /etc, que geralmente são gravados em uma unidade de disco, o diretório /proc é um pseudo sistema de arquivos mantido na memória do computador.
•	O subdiretório /proc/sys contém pseudo arquivos que podem ser usados para alterar as configurações do kernel em execução.
•	Como esses arquivos não são arquivos "reais", um editor não deve ser usado para alterá-los; em vez disso, você deve usar um comando echo ou sysctl para substituir o conteúdo desses arquivos.
•	Pelo mesmo motivo, não tente exibir esses arquivos em um editor, mas use o comando cat ou sysctl.
•	Para alterações permanentes na configuração, o kernel usa o arquivo /etc/sysctl.conf normalmente, esse arquivo é usado pelo kernel para fazer alterações nos arquivos /proc quando o sistema está inicializando.
•	Lembre-se de que os diretórios que possuem números para nomes representam processos em execução no sistema.
•	O primeiro processo é sempre /sbin/init, portanto, o diretório /proc/1 conterá arquivos com informações sobre o processo init em execução .
•	O arquivo cmdline dentro do diretório do processo /proc/1/cmdline, por exemplo, mostrará o comando que foi executado.
•	A ordem na qual outros processos são iniciados varia muito de sistema para sistema.
•	Como o conteúdo desse arquivo não contém um novo caractere de linha, um comando echo será executado para fazer com que o prompt vá para uma nova linha.
•	o arquivo /dev/null (que é comumente conhecido como bit bucket).
•	Um processo executado em primeiro plano impedirá o usuário de usar o shell até que o processo seja concluído.
•	Por outro lado, um processo executado em segundo plano permitirá que o usuário use o shell e execute outros comandos.
•	O sistema continuará executando até que o processo seja encerrado ou suspenso pelo usuário.
◦	Para terminar o processo de primeiro plano, pressione Ctrl – C.
◦	Para iniciar o mesmo processo em segundo plano, digite: (&) ao final do comando.
◦	Ao adicionar o  (&) comercial  ao final do comando, o processo é iniciado em segundo plano, permitindo ao usuário manter o controle do terminal.
◦	Ao executar:
◦	ping localhost> /dev/null &
▪	[1] 107
◦	Isso significa que esse processo possui um número de trabalho 1 (como demonstrado pela saída de [1]) e um ID do processo (PID) de 107.
◦	Cada terminal  /shell terá números de trabalho exclusivos.
◦	O PID é de todo o sistema; cada processo possui um número de identificação exclusivo.
◦	Essas informações são importantes ao executar determinadas manipulações de processos, como interromper processos ou alterar seu valor de prioridade.
•	Existem vários valores numéricos diferentes que podem ser enviados para um processo.
•	Estes são valores predefinidos, cada um com um significado diferente.
•	O prompt indica que o sinal padrão é o sinal de término indicado por SIGTERM ou o número 15.
•	Considere isto
◦	O sinal de interrupção 9 ou SIGKILL é um sinal "forte" que não pode ser ignorado, diferente do valor padrão de 15.
•	Logs do sistema:
◦	Os logs do sistema são críticos para muitas tarefas, incluindo a correção de problemas do sistema operacional e a garantia de segurança do sistema.
◦	Saber onde os arquivos de log do sistema estão armazenados e como mantê-los é importante para um administrador do sistema.
•	Existem dois daemons que manipulam mensagens de log:
◦	O syslogddaemon e o klogddaemon.
•	Normalmente você não precisa se preocupar klogd; ele lida apenas com mensagens de log do kernel e envia suas informações de log para o syslogddaemon.
•	As mensagens geradas pelo kernel no momento da inicialização são armazenadas no arquivo /var/log/dmesg.
•	O principal arquivo de log que está escrito pelos syslogd representa /var/log/mensagens.
•	Além do log realizado por syslogd, muitos outros processos executam seu próprio log.
•	Alguns exemplos de processos que fazem seu próprio log incluem o servidor da web Apache (o arquivo de log reside no diretório /var/log/httpd), o Common Unix Printing System ( /var/log/cups) e o auditddaemon ( /var/log/audit).
•	Nos sistemas CentOS, esso syslogd é chamado rsyslogd.


COMANDOS DE MANIPULACAO DE PROCESSOS E INFORMACOES DE HARDWARE

jobs
mostra todos os processos que estao sendo executados em segundo plano

fg %"num do processo"
Faz com que o processo em segundo plano venha para primeiro plano.

bg %"num do processo"
Faz com que o processo retorne a segundo plano.

comando kill %"num do processo"
Para a execucao do comando em especifico

killall "comando"
Para todos os processos de excucao de comandos

pkill "-valo numerico" "comando"
Encerra o processo utilizando o psedoumo do comando ao inves do PID.

top
Por padrão, o programa top classifica os processos em ordem decrescente da porcentagem de uso da CPU, para que os programas mais ocupados estejam no topo de sua lista.
•	A saída do comando top muda a cada 2 segundos.
•	O comando top é um programa interativo, o que significa que você pode emitir comandos dentro do programa.
•	digitando a letra k faz com que um prompt interativo apareca.

sleep
O comando sleep geralmente é usado para pausar um programa (shell script) por um período específico de tempo.
Nesse caso, é usado apenas para fornecer um comando que levará muito tempo para ser executado.

ps
Detalha informacoes do processo como PID
•	O comando ps pode ser usado para visualizar processos.
•	Por padrão, o comando ps exibirá apenas os processos em execução no shell atual.
◦	Opcao -e
▪	Faz com que todos os processos em execucao sejam exibidos.
◦	Opcao -o
▪	Especifica a coluna a ser exibida.

free
Mostra o uso geral da memoria
•	Opção -m
◦	Força a saída a ser arredondada para o megabyte mais próximo (MB).
•	Opção -g
◦	Força a saída a ser arredondada para o gigabyte mais próximo (GB):

dmesg
Permite visualizar as mensagens atuais do kernel, além de fornecer controle sobre se essas mensagens aparecerão em uma janela do console do terminal.

sysctl

lspci
Para visualizar todos os dispositivos conectados pelo barramento PCI
•	Opção -k
◦	Mostrar dispositivos junto com o driver do kernel e os módulos usados:

lsmod
Visualiza os módulos carregados no momento:

arch
Para ver a qual família a CPU do sistema atual pertence

lscpu
Para mais informações sobre a CPU

lsusb
Exibi os dispositivos conectados ao sistema via USB

umount

fdisk
Util para identificar e manipular recursos de armazenamento em disco em um sistema.
•	Podendo ser usado para criar, formatar e excluir partições, além de obter informações, deve ser usado com cuidado no modo administrador para evitar a perda de dados.
◦	Opção (-l)
▪	Listará de maneira não interativa os dispositivos de bloco, o que inclui discos (discos rígidos) e volumes lógicos.
◦	Sem a opção (-l)
▪	o comando fdisk entra em um modo interativo que normalmente é usado para modificar partições em um dispositivo de disco.

Parted

gparted



















```
