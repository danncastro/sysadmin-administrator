# DMZ - Demilitarized Zone

> **Recapitulando o que temos no sistema**

> Temos a **intranet**, em que estão as pessoas desenvolvedoras e que fica hospedado em algum servidor, por exemplo, o servidor de dados - o **Database** - e o servidor **web**. Para intermediar tudo isso, há um **Firewall** que estabelece regras de segurança, com um IDS e IPS embutidos para detectar e prevenir os ataques. Há, também, um **WAF** que funciona como um proxy reverso, sendo quem recebe as requisições e deixa o nosso IP privado para a rede pública.

No vídeo anterior, levantamos uma hipótese: se algum(a) funcionário(a) sofrer um ataque cibernético, terão acesso ao nosso sistema? Como, por exemplo, ao servidor de banco de dados.

Um mecanismo para implementarmos para evitar isso, seria o **DMZ** (_Demilitarized Zone_, em português "Zona Desmilitarizada"). Nós separaríamos toda rede externa da interna, sendo a externa a que fica à frente da internet (WAF) e uma interna, do lado do Database.

![Diagrama visual do funcionamento entre intranet, internet, Server Web, Database, Firewall, WAF e DMZ. Na parte central do diagrama, há o ícone do Firewall, com a escrita "Firewall" abaixo. Este possui cinco setas: uma que aponta para a parte inferior, em que temos um ícone de servidor com uma nuvem, escrito "Intranet" abaixo; outra aponta para cima, em que há o ícone de um servidor da internet com o escrito "internet", abaixo; outra que aponta para à esquerda, em que há um ícone do Server Web, com o escrito "Web", em azul abaixo e com o escrito "DMZ Web" acima e outra, também para a esquerda, que aponta para o Database com o escrito "DMZ Banco"; e, por último, uma seta que aponta para à direita com um ícone de servidor escrito "WAF" abaixo e com o escrito "DMZ Externa", acima.](https://cdn1.gnarususercontent.com.br/1/723333/1aa42e36-f81e-4e35-a84d-95c39122ea28.png)

Com isso, separamos em zonas: na externa, o WAF e na interna, o Database -DMZ Banco- e a Web - DMZ Web. Ou seja, vamos separar em sub-redes, para evitar que caso tenha algum ataque, que possua acesso a todas as informações do nosso sistema.

Esta aula foi bem teórica, dado que precisamos entender bem a implementação de diversos mecanismos. No próximo vídeo, vamos simular todos esses mecanismos na rede.
