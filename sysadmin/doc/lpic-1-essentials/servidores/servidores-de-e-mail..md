---
description: >-
  Ao discutir servidores de email, e sempre útil examinar as três tarefas
  diferentes necessárias para receber email entre as pessoas.
---

# Servidores de e-mail.

### (MTA) Agente de Transferência de Correio&#x20;

#### Sendmail

O MTA mais conhecido (software usado para transferir mensagens eletrônicas para outros sistemas) é o Sendmail .&#x20;

#### Postfix

O Postfix é outro popular e tem como objetivo ser mais simples e mais seguro que o Sendmail.

### (MDA) Agente de Entrega de Correio&#x20;

Também chamado de Agente de Entrega Local , ele cuida de armazenar o email na caixa de correio do usuário.&#x20;

{% hint style="info" %}
Geralmente invocado a partir do MTA final na cadeia.
{% endhint %}

### Servidor POP / IMAP

O POP (Protocolo da agência postal) e o IMAP (Internet Message Access Protocol) são dois protocolos de comunicação que permitem que um cliente de email em execução no seu computador fale com um servidor remoto para receber o email.
