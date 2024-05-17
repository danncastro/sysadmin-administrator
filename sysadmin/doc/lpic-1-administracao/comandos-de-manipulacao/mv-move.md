---
description: Utilizado para mover arquivos e diretórios.
---

# mv (Move)

A sintaxe para o comando `mv` é muito parecida com o comando `cp`

```bash
mv [fonte] [destino]
```

> FONTE e o arquivo ou diretório a ser movido.&#x20;

Quando um arquivo é movido, ele é removido do local original e colocado em um novo local.&#x20;

Mover arquivos pode ser um pouco complicado no Linux porque os usuários precisam de permissões específicas para remover arquivos de um diretório. Sem as permissões corretas, uma mensagem de erro é retornada&#x20;

{% hint style="danger" %}
"Permission denied"
{% endhint %}

O comando `mv` tem como principais opções:&#x20;

`-i` Interativo - Pergunte se um arquivo deve ser substituído.

`-n` No Clobber - Não substitua o conteúdo de um arquivo de destino.&#x20;

`-v` Detalhado -  Mostre a movimentação resultante.&#x20;

> Também pode ser digitado como (--verbose)

Não há opção `-r`, pois o comando `mv` move os diretórios por padrão.
