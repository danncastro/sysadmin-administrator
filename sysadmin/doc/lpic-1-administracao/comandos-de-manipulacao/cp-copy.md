---
description: Usado para copiar arquivos.
---

# cp (Copy)

Requer uma "fonte" e um "destino". A estrutura do comando é a seguinte:

```bash
cp [fonte] [destino]
```

1. A fonte é o arquivo a ser copiado.&#x20;
2. O destino é o local onde a cópia deve ser localizada.

{% hint style="info" %}
Quando bem-sucedido, o comando `cp` não possui saída.&#x20;
{% endhint %}

O comando a seguir copia o arquivo (/etc/hosts) para o diretório inicial `~`:&#x20;

```bash
cp /etc/hots ~
```

A opção `-v`  significa detalhado e faz com que o comando `cp` produza saída se for bem-sucedido.&#x20;

> Quando o destino é um diretório, o novo arquivo resultante mantém o mesmo nome que o arquivo original.

Para dar um novo nome ao novo arquivo, forneça o novo nome como parte do destino.&#x20;

Por Exemplo:&#x20;

```bash
cp /etc/hots ~/hots.copy
```

> O comando `cp` pode ser destrutivo para os dados existentes se o arquivo de destino já existir.

A opção `-i` requer que você responda **"y"** ou **"n"** para cada cópia que possa acabar substituindo o conteúdo de um arquivo existente. Com a opção interativa `-i`, o comando `cp` solicita ao usuário antes de substituir um arquivo.&#x20;

O exemplo a seguir demonstra essa opção:&#x20;

```bash
cp -i /etc/hots exemple.txt
```

> Para responder **"n"** a cada prompt automaticamente, use a opção `-n`. Significa não destruir ou substituir.&#x20;

Por padrão, o comando `cp` não copiará diretórios; qualquer tentativa de fazer isso resulta em uma mensagem de erro. No entanto, a opção `-r` do comando `cp` pode copiar arquivos e diretórios.

{% hint style="warning" %}
Tenha cuidado com esta opção: Toda a estrutura de diretórios será copiada, o que pode resultar na cópia de muitos arquivos e diretórios.
{% endhint %}

O comando `cp` tem como principais funcoes:&#x20;

`-i` Interativo - Pergunte se um arquivo deve ser substituído.

`-n` No Clobber - Não substitua o conteúdo de um arquivo de destino.&#x20;

`-v` Detalhado -  Mostre a movimentação resultante.&#x20;

> Também pode ser digitado como (--verbose)

`-r` Recursive - Copia diretórios.&#x20;

> Também pode ser digitado como -R (Maiúsculo).&#x20;

`-p` - Preserva os atributos do arquivo.
