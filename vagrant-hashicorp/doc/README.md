---
description: >-
  Ferramenta para automatizar configurações, desenvolvida pela Hashicorp na qual
  podemos provisionar uma infraestrutura de servidores e até mesmo
  configura-las.
---

# Introdução ao Vagrant Hashicorp

O Vagrant utiliza a linguagem _**HCL (Hashicorp Configuration Language)**_ que é de fácil entendimento **(baseada em Ruby)** e permite que possamos definir recursos da máquina virtual tais como **hostname, ip, cpu, memória, disco, quantidade de máquinas a serem criadas e scripts a serem executados**.

O Vagrant precisa de um Provider , que geralmente é um _**Hypervisor (Virtualbox, KVM, HyperV, VMWare, etc...)**_, que será utilizado como base para fornecer os recursos de virtualização, podemos dizer que o Vagrant é como se fosse um frontend em CLI que utiliza os hypervisors como um backend para executar suas tarefas.&#x20;

Existem dois tipos de **Hypervisors:** Tipo 1 e Tipo 2.

{% hint style="info" %}
Os Hypervisors do Tipo 1 são chamados de **"bare metal"**, pois são executados diretamente no hardware do host. Exemplos disso são Hyper-V e vSphere (entre vários outros).
{% endhint %}

{% hint style="info" %}
Os Hypervisors do Tipo 2 rodam como uma aplicação em cima do sistema operacional. Exemplos são o VirtualBox e VMware.
{% endhint %}

Para executar as ações o Vagrant trabalha com dois papéis distintos: Provider e Provisioner

***
