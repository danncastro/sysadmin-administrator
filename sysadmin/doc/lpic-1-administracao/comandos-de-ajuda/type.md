---
description: >-
  Usado para exibir informações sobre os tipos de outros comandos. E um comando
  embutido do bash.
---

# type

{% hint style="info" %}
Bash e o interpretador de comandos mais usado no Linux.
{% endhint %}

> _Serve para informar se é um comando ou programa e de que tipo._

Exemplo:

#### <mark style="color:blue;">**Alias:**</mark>&#x20;

Um apelido. Geralmente um nome mais curto para memorizar.&#x20;

#### <mark style="color:blue;">Comando interno do Shell:</mark>&#x20;

Um comando embutido ao bash ou a outro shell; Quando o comando e interno ao shell ele e conhecido como built-in.&#x20;

#### <mark style="color:blue;">Comando externo do Shell:</mark>&#x20;

Um comando que não faz parte do shell,  mas é um arquivo localizado no sistema de arquivos

* Geralmente dentro das pastas: `/bin/, sbin/, usr/bin … etc.`

Quando o comando e externo o do shell o `type` retorna seu caminho.&#x20;

* Opção mais usada no comando type: `-t` Abrevia o resultado.

***
