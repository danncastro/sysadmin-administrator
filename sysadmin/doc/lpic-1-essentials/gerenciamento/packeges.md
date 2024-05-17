---
description: >-
  Ferramentas utilizadas para o gerenciamento de pacotes em diversas
  Distribuições Linux;
---

# Packeges

## Debian

> A ferramenta de nível mais baixo (backend) para gerenciar esses arquivos no debian e o comando **dpkg**.

### apt (Advanced Package Tool)&#x20;

* Programa front-end da ferramenta dpkg&#x20;

### aptitude&#x20;

* Ferramenta adicional de linha de comando que servem como front-end para o dpkg&#x20;

### Synaptic&#x20;

* Ferramenta front-end da GUI&#x20;

### Software Centrer.&#x20;

* Ferramenta front-end da GUI&#x20;

## RedHat

O Linux Standards Base , que é um projeto Linux Foundation , foi projetado para especificar (por consenso) um conjunto de padrões que aumentam a compatibilidade entre os sistemas Linux em conformidade. De acordo com a Linux Standards Base, o sistema padrão de gerenciamento de pacotes é o RPM.&#x20;

> O RPM utiliza um arquivo `.rpm` para cada pacote de software.&#x20;

Este sistema e o que as distribuições derivadas do Red Hat, incluindo CentOS e Fedora, usam para gerenciar seus softwares.&#x20;

Outras distribuições não derivadas da Red Hat, como SUSE, OpenSUSE e Arch Linux, também utilizam pacotes RPM.&#x20;

> A ferramenta de backend mais comumente usada para gerenciamento de Pacotes RPM e o comando **rpm**.&#x20;

Embora o comando rpm possa instalar, atualizar, consultar e remover pacotes, há ferramentas de front-end de linha de comando&#x20;

### yum e up2date&#x20;

Automatizam o processo na resolução de problemas de dependência.&#x20;

As ferramentas front-end da GUI mais conhecidas são:&#x20;

### Yumex e Gnome PackageKit

Facilitam o gerenciamento de pacotes RPM. Algumas distribuições baseadas em RPM implementaram o estilo de gerenciamento de pacotes ZYpp ou (libzypp) principalmente OpenSUSE e SUSE Linux Enterpris.&#x20;

### Zypper

O comando zypper e a base do método ZYpp e possui comandos longos escritos em inglês para executar funcoes, como a instalação de um pacote incluindo as dependências necessárias:&#x20;

```bash
zypper in package_name.
```

