---
description: O comando tar e usado para mesclar vários arquivos em um único arquivo.
---

# tar

> Por padrão, ele não compacta os dados.

Sua sintaxe e a seguinte:

```bash
tar -c [-f ARQUIVO] [OPÇÕES] [ARQUIVO…]
```

> O argumento ARQUIVO será o nome do arquivo resultante

`-c` - Informa ao comando `tar` para criar um arquivo `.tar`

`-v` - Significa “detalhado”, que institui o comando `tar` a demonstrar o que esta fazendo.

`-f` - Usada para especificar o nome de um arquivo `tar.`

`-t` - Usado para listar o conteúdo do arquivo em formato de lista.&#x20;

`-z` - Esta opção utiliza o `gzip` para executar a compactação.&#x20;

`-j` - Esta opção utiliza o `bzip2` para executar a compactação.&#x20;

`-x` - Extrai o conteúdo de um arquivo tar.&#x20;

`-r` - Adiciona um arquivo a um arquivo existente

{% hint style="info" %}
Não e necessário usar a extensão `.tar` no nome de arquivo morto, no entanto, e útil para identificar o tipo de arquivo.
{% endhint %}

> E considerado “Boas praticas” ao enviar um arquivo morto para outra pessoa.
