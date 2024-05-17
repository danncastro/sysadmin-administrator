# Backup2

seguranca do sistema e usuario

Contas administrativas Existem muitas maneiras diferentes de executar um comando que requer privilégios administrativos ou raiz. Efetuar login no sistema como usuário root permite executar comandos como administrador. Esse acesso é potencialmente perigoso, pois você pode esquecer que está logado como root e pode executar um comando que pode causar problemas no sistema. Como resultado, não é recomendável efetuar login diretamente como usuário ro Como o uso da conta root é potencialmente perigoso, você só deve executar comandos como root se forem necessários privilégios administrativos. Se a conta root estiver desativada, como está na distribuição Ubuntu, os comandos administrativos poderão ser executados usando o sudocomando Se a conta raiz estiver ativada, um usuário comum poderá executar o sucomando para alternar as contas para a conta raiz.

Quando você efetua login no sistema diretamente como root para executar comandos, tudo sobre sua sessão é executado como usuário root. Se estiver usando o ambiente gráfico, isso é especialmente perigoso, pois o processo de login gráfico é composto por muitos executáveis ​​diferentes (programas executados durante o login). Cada programa executado como usuário raiz representa uma ameaça maior do que um processo executado como usuário padrão, pois esses programas poderiam fazer quase qualquer coisa, enquanto os programas de usuário padrão são muito restritos no que podem fazer.

O outro perigo potencial ao fazer login no sistema como root é que uma pessoa que faz isso pode esquecer de fazer logout para executar seu trabalho não administrativo, permitindo que programas como navegadores e clientes de email sejam executados como usuário root sem restrições sobre o que eles poderiam fazer. O fato de várias distribuições do Linux, principalmente o Ubuntu, não permitirem que os usuários efetuem login como usuário root deve ser suficiente para indicar que essa não é a maneira preferida de executar tarefas administrativas.

15.2.1 Alternando usuários O sucomando permite executar um shell como um usuário diferente. Enquanto mudar para o rootusuário é o que osu usada com mais frequência, o comando também pode ser alterado para outros usuários.

su \[ opções ] \[ nome de usuário ]

Ao alternar usuários utilizando o shell de login opção de é recomendado, pois o shell de login configura completamente o novo shell com as configurações do novo usuário, garantindo que todos os comandos executados sejam executados corretamente. Se essa opção for omitida, o novo shell alterará o UID, mas não fará o login completo do usuário. A opção de shell de login pode ser especificada de uma de três maneiras:

su - su -l su --login

Por padrão, se um nome de usuário não for especificado, o sucomando abrirá um novo shell como o rootusuário. Os dois comandos a seguir são maneiras equivalentes de iniciar um shell como rootusuário:

su - raiz su -

Depois de pressionar Enter para executar um desses comandos, o usuário deve fornecer a senha do rootusuário para iniciar o novo shell. Se você não souber a senha da conta para a qual está mudando, então osu comando falhará.

Depois de usar o shell iniciado pelo sucomando para executar as tarefas administrativas necessárias, retorne ao seu shell original (e conta de usuário original) usando o exitcomando

Executando comandos privilegiados

O sudocomando permite que os usuários executem comandos como outro usuário. Semelhante ao sucomando, o rootusuário é assumido por padrão.

comando sudo \[ opções ]

Nas distribuições que não permitem que o rootusuário efetue login diretamente ou por meio do sucomando, o processo de instalação configura automaticamente uma conta de usuário para poder usar o sudocomando para executar comandos como se o rootusuário os executasse. Por exemplo, privilégios administrativos são necessários para visualizar o /etc/shadowarquivo:

Ao usar o sudocomando para executar um comando como rootusuário, o comando solicita a senha do próprio usuário, não a senha do rootusuário. Esse recurso de segurança pode impedir o acesso administrativo não autorizado se o usuário deixar seu computador sem vigilância. O prompt para a senha não aparecerá novamente enquanto o usuário continuar executando sudocomandos com menos de cinco minutos de intervalo.

O uso do sudocomando para executar um comando administrativo resulta em uma entrada colocada em um arquivo de log. Cada entrada inclui o nome do usuário que executou o comando, o comando que foi executado e a data e hora da execução. Isso permite maior responsabilidade, em comparação com um sistema em que muitos usuários podem conhecer a rootsenha e podem efetuar login diretamente como rootou usar o sucomando para executar comandos como o rootusuário.

Uma grande vantagem do uso sudopara executar comandos administrativos é que reduz o risco de um usuário executar acidentalmente um comando como root. A intenção de executar um comando é clara; o comando é executado como rootse precedido pelo sudocomando Caso contrário, o comando é executado como um usuário comum

Contas de usuário

Existem vários arquivos de texto no /etcdiretório que contêm os dados da conta dos usuários e grupos definidos no sistema. Por exemplo, para verificar se uma conta de usuário específica foi definida no sistema, o local a ser verificado é o /etc/passwdarquivo.

O /etc/passwdarquivo define algumas informações da conta para contas de usuário. O exemplo a seguir mostra as últimas cinco linhas de um /etc/passwdarquivo típico :

Cada linha contém informações pertencentes a um único usuário. Os dados são separados em campos por caracteres de dois pontos. A seguir, descrevemos cada um dos campos em detalhes, da esquerda para a direita, usando a última linha da saída do gráfico anterior:

Nome "sysadmin" : x: 1001: 1001: Administrador do Sistema ,,,,: / home / sysadmin: / bin / bash O primeiro campo contém o nome do usuário ou o nome de usuário . Este nome é usado ao efetuar login no sistema e quando a propriedade do arquivo é visualizada com o ls -lcomando Ele é fornecido para facilitar a referência de usuários comuns à conta, enquanto o sistema normalmente utiliza o ID do usuário internamente.

Espaço reservado da senha sysadmin: "x" : 1001: 1001: Administrador do Sistema ,,,,: / home / sysadmin: / bin / bash Ao mesmo tempo, a senha do usuário foi armazenada nesse local, no entanto, agora o xcampo neste indica ao sistema que a senha está no /etc/shadowarquivo.

ID do usuário sysadmin: x: "1001" : 1001: Administrador do Sistema ,,,,: / home / sysadmin: / bin / bash Cada conta recebe um ID do usuário (UID) . Os nomes de usuários não são usados ​​diretamente pelo sistema, que normalmente define a conta pelo UID. Por exemplo, os arquivos pertencem a UIDs, não a nomes de usuários.

ID do grupo principal sysadmin: x: 1001: "1001" : Administrador do Sistema ,,,,: / home / sysadmin: / bin / bash Este campo indica que o usuário é um membro desse grupo, o que significa que o usuário tem permissões especiais em qualquer arquivo pertencente a esse grupo.

Comente sysadmin: x: 1001: 1001: "Administrador do Sistema" ,,,, : / home / sysadmin: / bin / bash Este campo pode conter qualquer informação sobre o usuário, incluindo o nome real ou outras informações úteis.

Diretório Inicial sysadmin: x: 1001: 1001: Administrador do Sistema ,,,,: "/ home / sysadmin" : / bin / bash Este campo define o local do diretório inicial do usuário. Para usuários regulares, isso normalmente seria . Por exemplo, um nome de usuário de teria um diretório inicial de ./home/usernamebob/home/bob

O usuário root geralmente possui um local diferente para o diretório pessoal, o /rootdiretório.

shell sysadmin: x: 1001: 1001: Administrador do Sistema ,,,,: / home / sysadmin: "/ bin / bash" Este campo indica a localização do shell de login do usuário. Por padrão, o usuário é colocado nesse shell sempre que faz login em um ambiente de linha de comando ou abre uma janela de terminal. O shell bash /bin/bashé o shell mais comum para usuários do Linux

Senhas Como mencionado anteriormente, o /etc/shadowarquivo contém informações da conta relacionadas à senha do usuário. No entanto, usuários regulares não podem exibir o conteúdo do /etc/shadowarquivo por razões de segurança. Para visualizar o conteúdo deste arquivo, efetue login como administrador (a conta raiz):

Novamente, cada linha é separada em campos por caracteres de dois pontos. A seguir, descrevemos cada um dos campos em detalhes, da esquerda para a direita, usando a última linha da saída do gráfico anterior:

Nome do usuário "sysadmin" : $ 6 $ c75ekQWF $ .GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ / 221QL5AX5RjKXpXPJRQ0uVN35TY3 / .. c7v0.n0: 16874: 5: Este campo contém o nome de usuário da conta, que corresponde ao nome da conta no /etc/passwdarquivo.

Senha sysadmin: "$ 6 $ c75ekQWF $ .GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ / 221QL5AX5RjKXpXPJRQ0uVN35TY3 / .. c7v0.n0 :" 16874: 5: O campo senha contém a senha criptografada da conta. Essa sequência muito longa é uma criptografia unidirecional, o que significa que não pode ser "revertida" para determinar a senha original. Enquanto usuários regulares possuem senhas criptografadas nesse campo, as contas do sistema possuem um \*caractere asterisco nesse campo.

Última mudança sysadmin: $ 6 $ c75ekQWF $ .GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ / 221QL5AX5RjKXpXPJRQ0uVN35TY3 / .. c7v0.n0: "16874" : 5: Este campo contém um número que representa a última vez que a senha foi alterada. O número 16874é o número de dias desde 1º de janeiro de 1970 (chamado de época). Este valor é gerado automaticamente quando a senha do usuário é modificada. É usado pelos recursos de duração da senha fornecidos pelo restante dos campos deste arquivo.

Mínimo sysadmin: $ 6 $ c75ekQWF $ .GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ / 221QL5AX5RjKXpXPJRQ0uVN35TY3 / .. c7v0.n0: 16874: "5" : Este campo indica o número mínimo de dias entre as alterações de senha. É um dos campos de validade da senha ; um valor diferente de zero nesse campo indica que, depois que um usuário altera sua senha, a senha não pode ser alterada novamente pelo número especificado de dias, 5dias neste exemplo. Este campo é importante quando o campo máximo é usado. Um valor zero neste campo significa que o usuário sempre pode alterar sua senha.

Máximo administrador de sistema: $ 6 $ $ c75ekQWF .GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ / 221QL5AX5RjKXpXPJRQ0uVN35TY3 / .. c7v0.n0: 16874: 5: "30" : 7: 60: 15050: Este campo indica o número máximo de dias em que a senha é válida. É usado para forçar os usuários a alterar suas senhas regularmente. Um valor 30nesse campo significa que o usuário deve alterar sua senha pelo menos a cada 30 dias para evitar que sua conta seja bloqueada.

Observe que, se o campo mínimo estiver definido como 0, o usuário poderá definir sua senha imediatamente de volta ao valor original, anulando o propósito de forçar o usuário a alterar sua senha a cada 30 dias. Portanto, se o campo máximo estiver definido, o campo mínimo também será normalmente definido.

Por exemplo, no mínimo : máximo de 5:30meios que o usuário deve alterar sua senha a cada 30 dias e, após a alteração, o usuário deve aguardar 5 dias para poder alterar sua senha novamente.

Se o maxcampo estiver definido como 99999o valor máximo possível, o usuário basicamente nunca precisará alterar sua senha (porque 99999 dias são aproximadamente 274 anos).

Advertir administrador de sistema: $ 6 $ $ c75ekQWF .GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ / 221QL5AX5RjKXpXPJRQ0uVN35TY3 / .. c7v0.n0: 16874: 5: 30: "7" : 60: 15050 :: O usuário é avisado apenas no logon; portanto, alguns administradores adotaram a abordagem de definir o campo warn como um valor mais alto para fornecer uma chance maior de emitir um aviso.

Se o período máximo estiver definido como 99999, o campo de aviso será basicamente inútil.

Inativo administrador de sistema: $ 6 $ $ c75ekQWF .GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ / 221QL5AX5RjKXpXPJRQ0uVN35TY3 / .. c7v0.n0: 16874: 5: 30: 7: "60" : 15050 :: Se o usuário ignorar os avisos e exceder o prazo da senha, sua conta será bloqueada. Nesse caso, o campo inativo fornece ao usuário um período de "cortesia" no qual sua senha pode ser alterada, mas apenas durante o processo de login.

Se o campo inativo estiver definido como 60, o usuário terá 60 dias para mudar para uma nova senha. Se eles não conseguirem, o administrador seria necessário para redefinir a senha do usuário.

Expirar administrador de sistema: $ 6 $ $ c75ekQWF .GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ / 221QL5AX5RjKXpXPJRQ0uVN35TY3 / .. c7v0.n0: 16874: 5: 30: 7: 60: "15050" :: Este campo indica o dia em que a conta expirará , representada pelo número de dias a partir de 1º de janeiro de 1970. Uma conta expirada está bloqueada, não excluída, o que significa que o administrador pode redefinir a senha para desbloquear a conta. Contas com datas de vencimento geralmente são fornecidas a funcionários ou contratados temporários. A conta expira automaticamente após o último dia de trabalho do usuário. Quando um administrador define esse campo, uma ferramenta é usada para converter de uma data real para uma data da época. Existem também vários conversores gratuitos disponíveis na Internet.

Reservado administrador de sistema: $ 6 $ $ c75ekQWF .GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ / 221QL5AX5RjKXpXPJRQ0uVN35TY3 / .. c7v0.n0: 16874: 5: 30: 7: 60: 15050 "::" Atualmente não usado, este campo está reservado para uso futuro.

Considere isto

Além do grepcomando, outra técnica para recuperar as informações do usuário contidas nos arquivos /etc/passwde /etc/shadowé usar o getentcomando Uma vantagem desse comando é que ele pode recuperar informações da conta definidas localmente, em arquivos como /etc/passwde /etc/shadowou em um servidor de diretório de rede.

A sintaxe geral de um getentcomando é:

getent database record

Contas do sistema Os usuários efetuam login no sistema usando contas de usuário regulares. Normalmente, essas contas têm valores de UID maiores que 500 (em alguns sistemas 1.000). O usuário root tem acesso especial ao sistema. Esse acesso é fornecido à conta com um UID 0.

Existem contas adicionais que não foram projetadas para os usuários efetuarem login. Essas contas, geralmente do UID 1 ao UID 499, são chamadas de contas do sistema e são projetadas para fornecer contas de serviços em execução no sistema.

As contas do sistema possuem alguns campos nos arquivos /etc/passwde /etc/shadowque são diferentes de outras contas. Por exemplo, as contas do sistema raramente têm diretórios pessoais, pois geralmente não são usadas para criar ou armazenar arquivos. No /etc/passwdarquivo, as contas do sistema têm um programa sem login no campo shell :

sshd: x: 103: 65534 :: / var / run / sshd: "/ usr / sbin / nologin"

No /etc/shadowarquivo, as contas do sistema geralmente têm um caractere asterisco \* no lugar do campo de senha: sshd: \* : 16874: 0: 99999: 7 :::

A maioria das contas do sistema é necessária para que o sistema funcione corretamente. Você não deve excluir uma conta do sistema, a menos que tenha certeza de que a remoção da conta não causará problemas. Reserve um tempo para aprender o que cada conta do sistema faz; Os administradores de sistema têm a tarefa de garantir a segurança do sistema, e isso inclui a proteção adequada das contas do sistema.

Contas de grupo Seu nível de acesso a um sistema não é determinado apenas por sua conta de usuário. Cada usuário pode ser membro de um ou mais grupos , o que também pode afetar o nível de acesso ao sistema.

Tradicionalmente, os sistemas UNIX limitavam os usuários a pertencerem a não mais de um total de dezesseis grupos, mas os kernels recentes do Linux oferecem suporte a usuários com mais de sessenta e cinco mil associações a grupos.

O /etc/passwdarquivo define a associação do grupo principal para um usuário. Associação suplementar ao grupo (ou associação secundária ao grupo) e os próprios grupos são definidos no /etc/grouparquivo.

O /etc/grouparquivo é outro arquivo delimitado por dois pontos. A seguir, são descritos os campos com mais detalhes, usando uma linha que descreve uma conta de grupo típica.

Nome do grupo "mail" : x: 12: mail, postfix Este campo contém o nome do grupo . Como nos nomes de usuário, os nomes são mais naturais para as pessoas se lembrarem do que os números. O sistema geralmente usa IDs de grupo em vez de nomes de grupo.

Espaço reservado da senha mail: "x" : 12: mail, postfix Embora existam senhas para grupos, elas raramente são usadas no Linux. Se o administrador criar uma senha de grupo, ela será armazenada no /etc/gshadowarquivo. O xcampo neste campo é usado para indicar que a senha não está armazenada neste arquivo.

GID mail: x: "12" : mail, postfix Cada grupo está associado a um ID de grupo exclusivo (GID), que é colocado neste campo.

Lista de usuários mail: x: 12: "mail, postfix" Este último campo é usado para indicar quem é membro do grupo. Enquanto a associação ao grupo principal estiver definida no /etc/passwdarquivo, os usuários atribuídos a grupos adicionais terão seu nome de usuário colocado neste campo do /etc/grouparquivo. Nesse caso, os usuários maile postfixsão membros secundários do mailgrupo.

Para visualizar informações sobre um grupo específico, os comandos grepou getentpodem ser usados.

Visualizando informações do usuário

 O idcomando é usado para imprimir informações de usuário e grupo para um usuário especificado.

id \[ opções ] nome de usuário

Ao alternar entre diferentes contas de usuário, pode ser confuso qual conta está conectada no momento. Quando executado sem argumento, o idcomando gera informações sobre o usuário atual, permitindo que você confirme sua identidade no sistema.

A saída do idcomando sempre lista as informações da conta do usuário primeiro, usando o ID do usuário e o nome do usuário primeiro: "uid = 1001 (sysadmin)" gid = 1001 (sysadmin) grupos = 1001 (sysadmin), 4 (adm), 27 (sudo)

Após o nome de usuário, o grupo principal é listado, denotado pelo ID e pelo nome do grupo : uid = 1001 (sysadmin) :gid = 1001 (sysadmin)" grupos = 1001 (sysadmin), 4 (adm), 27 (sudo)

Outras informações listadas incluem os grupos aos quais o usuário pertence, denotado novamente pelos IDs do grupo seguidos pelos nomes dos grupos. O usuário mostrado pertence a três grupos: uid = 1001 (sysadmin) gid = 1001 (sysadmin) g"rupos = 1001 (sysadmin), 4 (adm), 27 (sudo)"

Se o comando receber um nome de usuário como argumento, por exemplo root, ele exibirá informações sobre a conta especificada:

Para imprimir apenas o grupo principal do usuário, use a -gopção: ‌

O idcomando também pode ser usado para verificar as participações em grupos secundários do usuário, para imprimir essas informações, use a -Gopção:

A saída do exemplo anterior está alinhada com o conteúdo do /etc/grouparquivo, conforme a pesquisa sysadminrevela:

Vendo usuários atuais

O whocomando exibe uma lista de usuários que estão atualmente conectados ao sistema, de onde estão e quando efetuaram login. Com o uso de opções, esse comando também pode exibir informações como o nível de execução atual (uma funcionalidade estado do computador) e a hora em que o sistema foi inicializado.

A seguir, descreve a saída do whocoma

Nome do usuário "root" tty2 2013-10-11 10:00 Esta coluna indica o nome do usuário que está logado. Observe que por "logado" queremos dizer "qualquer processo de logon e abrir a janela do terminal".

terminal root "tty2" 11-10-2013 10:00 sysadmin "pts / 0" 2013-10-11 09:59 (: 0.0) Esta coluna indica em qual janela do terminal o usuário está trabalhando.

Se o nome do terminal começar tty, isso é uma indicação de um logon local , pois esse é um terminal de linha de comando comum. Se o nome do terminal começar pts, isso indica que o usuário está usando um pseudo terminal ou executando um processo que atua como um terminal.

date root tty2 "2013-10-11 10:00" Esta coluna indica quando o usuário efetuou login.

host Após a data e a hora, algumas informações de localização podem aparecer. Se as informações de localização contiverem um nome de host, nome de domínio ou endereço IP, o usuário efetuou login remotamente : sysadmin pts / 1 11/10/2013 - 10:00 "(example.com)"

Se houver dois pontos e um número, isso indica que eles executaram um login gráfico local : sysadmin tty1 2013-10-11 09:59 "(: 0)"

Se nenhuma informação de localização for mostrada na última coluna, isso significa que o usuário efetuou login através de um processo de linha de comando local : root tty2 2013-10-11 10:00

Considere isto

O whocomando possui várias opções para exibir informações de status do sistema. Por exemplo, a -bopção mostra a última vez que o sistema foi iniciado (inicializado) e a -ropção mostra a hora em que o sistema atingiu o nível de execução atua

Pode haver casos em que são necessárias mais informações sobre os usuários e o que eles estão fazendo no sistema. O wcomando fornece uma lista mais detalhada sobre os usuários atualmente no sistema do que o whocomando. Ele também fornece um resumo do status do sistema. Por exemplo:

A primeira linha de saída do wcomando é idêntica à do uptimecomando. Ele mostra o horário atual, há quanto tempo o sistema está em execução, o número total de usuários atualmente conectados e a carga no sistema em média nos últimos períodos de 1, 5 e 15 minutos. A média de carga é a utilização da CPU em que um valor de 100 significaria o uso total da CPU durante esse período de tempo.

A seguir, descreve o restante da saída do wcomando:

Coluna Exemplo Descrição USER root O nome do usuário que está conectado. TTY tty2 Em qual janela do terminal o usuário está trabalhando. FROM example.com De onde o usuário efetuou login. LOGIN@ 10:00 Quando o usuário efetuou login. IDLE 43:44 Há quanto tempo o usuário está ocioso desde que o último comando foi executado. JCPU 0.01s O tempo total da CPU usado por todos os processos é executado desde o login. PCPU 0.01s O tempo total da CPU para o processo atual. WHAT -bash O processo atual que o usuário está executando. Nota: O scaractere representa segundos .

Visualizando o histórico de logon

O lastcomando lê todo o histórico de login do /var/log/wtmparquivo e exibe todos os logins e registros de reinicialização por padrão. Um detalhe interessante dos registros de reinicialização é que ele exibe a versão do kernel do Linux que foi inicializada em vez do local de login. O /var/log/wtmparquivo mantém um log de todos os usuários que efetuaram login e logout no sistema.

O lastcomando é um pouco diferente dos comandos whoe w. Por padrão, ele também mostra o nome de usuário, o terminal e o local de login, não apenas as sessões de login atuais, mas também as sessões anteriores. Ao contrário dos comandos whoe w, ele exibe a data e a hora em que o usuário efetuou login no sistema. Se o usuário tiver desconectado o sistema, ele exibirá o tempo total que o usuário passou conectado, caso contrário, será exibido still logged in.

Considere isto

O whocomando lê do /var/log/utmparquivo que registra os usuários atuais, enquanto o lastcomando lê do /var/log/wtmparquivo, que mantém um histórico de todos os logins do usuário.

O sucomando geralmente é usado para alternar usuários e iniciar um novo shell como outro usuário, sendo o padrão o usuário root. O sucomando é frequentemente usado quando uma série de comandos precisa ser executada como usuário root. Quando executado sem argumentos, o sucomando abre um novo shell como usuário root. Há alguma confusão sobre o que as iniciais “su” significam (usuário substituto, alternar usuário e superusuário são frequentemente referenciadas), mas o principal a ser observado é que ele permite que um administrador altere seu login para qualquer usuário no sistema.

O sudocomando geralmente é usado para executar um único comando como usuário root, prefixando esse comando sudo. O sudocomando deve ser configurado pelo usuário root antes que um usuário comum possa usá-lo. Por padrão, o sudocomando permanece em vigor por 15 minutos nos sistemas Ubuntu em que a conta raiz não é ativada por padrão. O sudocomando funciona em sistemas que não permitem acesso root por padrão. É preferível para a maioria das tarefas administrativas, pois o acesso root atinge o tempo limite automaticamente sem a necessidade de sair.\
O sistema solicitará a senha do usuário atual, não a senha root . Se o usuário atual fizer parte do sudogrupo, o comando será executado. Todos os comandos digitados pelos próximos 15 minutos serão executados como root por padrão nos sistemas Ubuntu. Outros sistemas podem ter tempos limite diferentes.

Importante

A senha que você forneceu era para sua conta sysadmin , não a conta raiz . Depois de sudoconfigurado para sua conta, você não precisa saber a rootsenha para executar sudocomandos como rootusuário.

Outra maneira de recuperar as informações da conta de um usuário é executando o seguinte comando: . O comando tem a vantagem sobre o comando, pois também pode acessar contas de usuário que não são definidas localmente. Em outras palavras, o comando pode obter informações do usuário para usuários que podem ser definidos em servidores de diretório de rede, como servidores LDAP, NIS, Domínio do Windows ou Domínio do Active Directory.getent passwd usernamegetentgrepgetent

Importante

Lembre-se de enquanto visualiza uma página de manual, pressione Enter para avançar linha por linha, espaço página por página e q para sair.

Nota

O arquivo /etc/group, juntamente com /etc/passwd, determina as associações ao seu grupo. Seu grupo principal padrão é determinado pela correspondência do seu GID encontrado /etc/passwdao GID definido para um grupo no /etc/group. Quaisquer associações de grupo secundárias são definidas no /etc/grouparquivo.

O formato das entradas no /etc/grouparquivo para cada linha é:

group\_name: senha: GID: user\_list

Você pode visualizar as informações da sua conta ou uma conta de usuário especificada usando o idcomando:
