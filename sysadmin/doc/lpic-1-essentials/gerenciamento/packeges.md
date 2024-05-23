---
description: >-
  Ferramentas utilizadas para o gerenciamento de pacotes em diversas
  Distribuições Linux;
---

# Packeges

***

## <mark style="color:red;">Debian</mark>

> A ferramenta de nível mais baixo (backend) para gerenciar esses arquivos no debian e o comando **dpkg**.

#### <mark style="color:blue;">apt (Advanced Package Tool)</mark>&#x20;

Programa front-end da ferramenta dpkg&#x20;

#### <mark style="color:blue;">aptitude</mark>&#x20;

Ferramenta adicional de linha de comando que servem como front-end para o dpkg&#x20;

#### <mark style="color:blue;">Synaptic</mark>&#x20;

Ferramenta front-end da GUI&#x20;

#### <mark style="color:blue;">Software Centrer.</mark>&#x20;

Ferramenta front-end da GUI&#x20;

***

## <mark style="color:red;">RedHat</mark>

O Linux Standards Base , que é um projeto Linux Foundation , foi projetado para especificar (por consenso) um conjunto de padrões que aumentam a compatibilidade entre os sistemas Linux em conformidade. De acordo com a Linux Standards Base, o sistema padrão de gerenciamento de pacotes é o RPM.&#x20;

> _O RPM utiliza um arquivo `.rpm` para cada pacote de software._&#x20;

Este sistema e o que as distribuições derivadas do Red Hat, incluindo CentOS e Fedora, usam para gerenciar seus softwares.&#x20;

Outras distribuições não derivadas da Red Hat, como SUSE, OpenSUSE e Arch Linux, também utilizam pacotes RPM.&#x20;

> _A ferramenta de backend mais comumente usada para gerenciamento de Pacotes RPM e o comando **rpm**._&#x20;

Embora o comando rpm possa instalar, atualizar, consultar e remover pacotes, há ferramentas de front-end de linha de comando&#x20;

#### <mark style="color:blue;">yum e up2date</mark>&#x20;

Automatizam o processo na resolução de problemas de dependência.&#x20;

As ferramentas front-end da GUI mais conhecidas são:&#x20;

#### <mark style="color:blue;">Yumex e Gnome PackageKit</mark>

Facilitam o gerenciamento de pacotes RPM. Algumas distribuições baseadas em RPM implementaram o estilo de gerenciamento de pacotes ZYpp ou (libzypp) principalmente OpenSUSE e SUSE Linux Enterpris.&#x20;

#### <mark style="color:blue;">Zypper</mark>

O comando zypper e a base do método ZYpp e possui comandos longos escritos em inglês para executar funcoes, como a instalação de um pacote incluindo as dependências necessárias:&#x20;

```bash
zypper in package_name.
```

***
