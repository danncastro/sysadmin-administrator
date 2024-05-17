# Firewall

Ao subirmos uma aplicação para a internet, estamos correndo diversos riscos de ataques, como: vazamento de dados, risco com a imagem da própria empresa que está subindo essa aplicação, problemas com os recursos de renda ou sistema, ao ser derrubado, entre outros ataques.

Diante disso, como podemos proteger as nossas aplicações na internet? Para isso, precisamos estabelecer alguns mecanismos nos nossos sistemas de rede, por exemplo, o _Firewall_.

O _**Firewall**_ (em portguês, "parede de fogo"), é uma barreira que protege a aplicação e a rede interna. Pensando em uma empresa, geralmente há uma equipe de desenvolvimento Back-end, uma de Front-end, QA, entre outras equipes. Portanto, sempre há uma rede privada, e o Firewall faz a proteção dessa rede e da nossa aplicação.

Além disso, o Firewall possui as funções de:

* Estabelecimento de um perímetro de segurança;

Isto é, como temos a rede privada e a pública (internet), ele estabelece esse perímetro de segurança entre a rede interna e externa.

* Separar as redes e controlar os acessos;
* Ser um elemento central de controle e aplicação de políticas de segurança;

Como está entre a rede pública e privada, será o elemento central e vai estabelecer algumas regras de segurança, como quem vai pode acessar determinado dado ou se houver algum comportamento suspeito, se poderá acessar a aplicação ou não.

* Proteger sistemas vulneráveis na rede;
* Aumentar a privacidade;
* Registrar e gerar estatísticas do uso da rede e acessos indevidos.

Em qual lugar o Firewall estará localizado no sistema? E a rede?

![Diagrama visual do funcionamento entre intranet, internet e Server Web. Na parte inferior há um ícone de um servidor com uma nuvem, com o texto "Intranet" abaixo. Este possui uma seta que aponta para cima para um ícone de outro servidor com uma nuvem, acompanhado do texto "Internet", abaixo. No meio da linha da seta apontando para cima, há uma linha para a horizontal esquerda com um ícone do Server Web, com o escrito "Server Web", em azul abaixo.](https://cdn1.gnarususercontent.com.br/1/723333/f36eb662-0b48-4eef-94f6-072cc8b499a5.png)

A Intranet é a rede privada, em que temos o setor de desenvolvimento da nossa aplicação. Geralmente, sobem isso em um servidor Web, como o NGINX e, em seguida, disponibilizam para toda a internet.

Porém, em qual lugar se localiza o Firewall?

![Diagrama visual do funcionamento entre intranet, internet, Server Web e Firewall. Na parte central do diagrama, há o ícone do Firewall, com o texto "Firewall" abaixo. Este possui três setas: uma que aponta para a parte inferior, em que temos um ícone de um servidor com uma nuvem, com o texto "Intranet" abaixo; outra seta que aponta para cima, em que há o ícone de um servidor da internet com o escrito "internet", abaixo; e, por último, uma que aponta para à esquerda, em que há um ícone do Server Web, com o escrito "Server Web", em azul abaixo.](https://cdn1.gnarususercontent.com.br/1/723333/e43cffbe-b619-4940-8e2d-f745e52def5d.png)

Por ser um elemento central, note que ele está no centro do diagrama! O Firewall será o responsável pelo controle de acesso da intranet, do nosso servidor e da internet. Contudo, somente ele é o suficiente para proteger toda a rede interna e a aplicação?
