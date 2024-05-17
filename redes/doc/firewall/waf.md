# WAF

**Recapitulando:** no nosso sistema temos a Intranet - em que se localiza todo o setor de desenvolvimento da aplicação - que estará hospedada em um servidor. Intermediando a conexão com a internet, temos o Firewall - responsável por monitorar quem possui acesso ou não à aplicação. Na Internet é onde estarão todos os usuários que podem acessar a nossa aplicação.

Suporemos que um atacante consegue passar, sem ser detectado pelo Firewall, e acessar a nossa aplicação. O que é possível incluirmos para aumentar a segurança, evitando esses casos? Tanto do lado do cliente quanto do servidor.

![Ilustração com três computadores à esquerda, todos possuem o domínio "example.com" escrito na tela e uma seta na cor azul apontando para à direita, para um ícone de servidor com o escrito "proxy" abaixo. Este possui uma seta azul, que aponta para uma nuvem, também na cor azul, que corresponde ao ícone da "internet". Este possui duas setas azuis: uma apontando para o ícone de Servidor de dados e a outra para o Servidor Web.](https://cdn1.gnarususercontent.com.br/1/723333/31e9e1fd-86bb-40fa-b1e0-db78bdf055df.png)

Vamos supor três usuários acessando o domínio "example.com". Geralmente a aplicação está hospedada em servidores: um de dados e outro de web. O que acontece no caminho quando enviamos uma requisição do domínio para o servidor? Intermediando essa comunicação, temos o _proxy_ - antes da requisição chegar na internet.

O _Proxy_ armazena o IP de origem da máquina dos clientes e ele passa, na internet, o IP dele mesmo. Com isso, ele protege o IP da máquina do usuário - dado que não é incluído na internet para um possível atacante. Assim que funciona, de forma bem resumida,o mecanismo de segurança do _proxy_, do lado do cliente.

![Ilustração com três computadores à esquerda, todos possuem o domínio "example.com" escrito na tela e uma seta na cor azul apontando para à direita, para uma nuvem na cor azul, que corresponde ao ícone da "internet". Este possui uma seta azul que aponta para o ícone de servidor com o escrito "proxy reverso". Este possui duas setas azuis: uma apontando para o ícone de Servidor de dados e a outra para o de Servidor Web.](https://cdn1.gnarususercontent.com.br/1/723333/6cc915f3-2336-4834-aa4a-e8b22b4eaefa.png)

E do lado do servidor? Será que o IP ficará disponível na internet? Para o lado do servidor, há outra categoria de proxy. Considerando o mesmo esquema dos três usuários, com os servidores Web e de dados, conseguimos montar um **proxy reverso**. Isso para armazenar e esconder o IP do servidor, passando para a internet somente o IP do _proxy_ reverso.

Além da segurança, o _proxy_ traz alguns benefícios para o nosso sistema:

* Balanceamento de carga;
* Proteção contra-ataques;
* Gerar os logs.

**Balanceamento de carga**

Tendo em vista que teremos requisições simultâneas, no **balanceamento de carga**, o _proxy_ reverso, pode passar um determinado servidor e, em seguida, para outro servidor. Isso para entregar a resposta.

Logo, vamos supor que há dois servidores web: o proxy pode, primeiro, solicitar para um dos servidores e, logo após, para o outro. Com isso, ele realiza o balanceamento da carga do sistema, evitando que o servidor seja derrubado pelo número de requisições simultâneas.

**Proteção contra-ataques**

A proteção contra-ataques ocorre pelo fato do IP de origem não ser disponibilizado na internet - somente o IP do proxy.

**Gerar os logs**

Como todo o tráfego passará pelo proxy, ele consegue registrar todas informações e gerar logs. Logs são importantes para realizarmos o monitoramento do tráfego e do que está acontecendo no sistema.

Para colocarmos isso na nossa rede, usaremos o **WAF (**_**Web application firewall**_**)**. O WAF funciona como um _proxy_ reverso, gerando os logs, realizando o balanceamento de carga e fazendo uma proteção a mais da nossa rede.

![Diagrama visual do funcionamento entre intranet, internet, Server Web, Firewall e WAF. Na parte central do diagrama, há o ícone do Firewall, acompanhado do texto "Firewall" abaixo. Este possui quatro setas: uma que aponta para a parte inferior, em que temos um ícone de servidor com uma nuvem, com o escrito "Intranet" abaixo; outra aponta para cima, em que há o ícone de um servidor da internet com o escrito "internet", abaixo; outra seta que aponta para à esquerda, em que há um ícone do Server Web, com o texto "Server Web", em azul abaixo. Por último, uma seta que aponta para à direita com um ícone de servidor escrito "WAF", abaixo.](https://cdn1.gnarususercontent.com.br/1/723333/63c69df8-4714-4501-90cd-c68fc01356ab.png)

Voltando para o nosso diagrama, perceba que incluímos o WAF à direita do Firewall. Isso para proteger os endereços IPs dos nossos servidores.

Aparentemente, a nossa rede está protegida: temos um Firewall, responsável pelas regras de segurança e o WAF, para a proteção do nosso IP - evitando **ataques de DoS**.

> Ataques DoS (_Denial of Service_, em português "Negação de serviço").

Em suma, ataques DoS é quando o atacante, ao descobrir o IP do servidor, realiza diversas requisições simultâneas até derrubar o sistema.

O WAF consegue nos proteger de vários ataques, **mas apenas na camada 7 do nosso modelo OSI** (_Open Systems Interconnection_, em português "Interconexão de Sistemas Abertos"). Em suma, o modelo OSI traz as camadas do percurso da requisição do nosso sistema até o servidor de origem da aplicação.

> [Para saber mais: tipos de WAF](https://cursos.alura.com.br/course/seguranca-rede-firewall-waf-siem/task/112829)

A camada 7 é a de aplicação, em que acontece os protocolos **HTTP** (_Hypertext Transfer Protocol_, em português "Protocolo de Transferência de Hipertexto"), serviço **DNS** (_Domain Name System_, em português "Sistema de nome de domínio") e o **FTP** (_File Transfer Protocol_ em português "Protocolo de Transferência de Arquivos"). Portanto, as outras camadas ficam vulneráveis.
