---
description: Remove arquivos
---

# rm (Remove)

Os arquivos são excluídos sem perguntas. Isso pode causar problemas ao excluir vários arquivos usando caracteres glob.&#x20;

{% hint style="warning" %}
Os arquivos são excluídos permanentemente.&#x20;
{% endhint %}

Não há comando para recuperar um arquivo e não há lixeira para recuperar arquivos excluídos.

Como precaução, os usuários devem usar a opção `-i` ao excluir vários arquivos:&#x20;

Por exemplo:&#x20;

```
rm -i *.txt
```

{% hint style="info" %}
O comando `rm` pode ser usado para excluir diretórios. No entanto, o comportamento padrão (sem opções) do comando `rm` é a não exclusão.&#x20;
{% endhint %}

> O comando `rm` pode ser usado para excluir diretórios. No entanto, o comportamento padrão (sem opções) do comando é á não exclusão.&#x20;

Para excluir um diretório com o comando `rm`, use a opção `-r` recursiva:&#x20;

Por exemplo:&#x20;

```
rm -r diretorio
```

Quando um usuário exclui um diretório, todos os arquivos e subdiretórios são excluídos sem nenhuma pergunta interativa.&#x20;

É melhor usar a opção `-i` com o comando `rm`.&#x20;

{% hint style="info" %}
Um diretório também pode ser excluído com o comando `rmdir`, mas apenas se o diretório estiver vazio.
{% endhint %}
