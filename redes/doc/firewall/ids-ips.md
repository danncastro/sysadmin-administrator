# IDS/IPS

Recapitulando o que temos na rede:

* **Intranet**: todo setor de desenvolvimento, que vai fazer uma aplicação hospedada no servidor web;
* **Firewall**: mediador que estabelece regras de segurança;
* **WAF**: camada de proteção para a rede, para não disponibilizar o IP na internet, realizar o balanceamento de cargas e gerar os logs;
* **Internet**: rede pública, em que estão todos os nossos usuários.

Para representar melhor, além do servidor web, temos o banco de dados - servidor de dados - à esquerda do Firewall no nosso esquema. Isso porque, geralmente, temos mais de um servidor com a aplicação.

![Diagrama visual do funcionamento entre intranet, internet, Server Web, Database, Firewall e WAF. Na parte central do diagrama, há o ícone do Firewall, com a escrita "Firewall" abaixo. Este possui cinco setas: uma que aponta para a parte inferior, em que temos um ícone de servidor com uma nuvem, escrito "Intranet" abaixo; outra aponta para cima, em que há o ícone de um servidor da internet com o escrito "internet", abaixo; outra que aponta para à esquerda, em que há um ícone do Server Web, com o escrito "Server Web", em azul abaixo e outra, também para a esquerda, que aponta para o Database; e, por último, uma seta que aponta para à direita com um ícone de servidor escrito "WAF", abaixo.](https://cdn1.gnarususercontent.com.br/1/723333/959f6955-4379-47f1-8b52-5719dfff4759.png)

Como é detectada uma invasão? Como é feita a seletividade do que pode acessar e o que não? E como barrar usuários com intenções maliciosas? Para isso, há mecanismos que podemos implementar.

> **IDS (**_**Intrusion Detection System**_**, em português "Sistema de Detecção de Intrusão")**

O IDS é um sistema que detecta a invasão ou comportamento suspeito na rede. Junto com ele, trabalha outro mecanismo, o **IPS (**_**Intrusion Prevention System**_**, em português "Sistema de Prevenção de Intrusão")**, sendo um sistema de prevenção. Logo, juntos, trabalham como se fosse o cérebro do sistema: detecta o que está um ataque e configuram o Firewall de forma automática para prevenir que o ataque ocorra.

Geralmente, o IDS e o IPS ficam no Firewall. Portanto, incluiremos algumas regras para ele reconhecer o que é um ataque. Com isso, parece que o nosso sistema já está bem seguro. Porém, na Intranet temos toda a nossa equipe de desenvolvimento da aplicação, supondo que algum funcionário sofra um ataque cibernético: será que esse ataque se estende por toda a nossa rede? Como prevenir esses ataques?
