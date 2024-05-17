---
description: 'As vantagens do mlocate são:'
---

# mlocate

Indexa todo o sistema de ficheiros. &#x20;

> Mas os resultados da pesquisa só incluem ficheiros a que o utilizador tem acesso.

Em vez de reler todo o conteúdo de todos os diretórios de cada vez que a base de dados e atualizada, o `mlocate` mantem informações temporais na sua base de dados e consegue determinar se o conteúdo dos diretórios foi alterado sem os ler novamente.&#x20;

Isso torna as atualizações muito mais rápidas e menos exigentes para o disco rígido.

{% hint style="info" %}
O banco de dados e criado por um outro utilitário chamado “`updatedb`”.
{% endhint %}
