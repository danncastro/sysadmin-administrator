---
description: >-
  Este comando e um filtro de texto que pesquisará linhas de entrada e retorno
  que contem uma correspondência com um determinado padrão.
---

# grep

Pode ser usado para filtrar linhas em um arquivo ou a saída de outro comando que corresponda a um padrão especificado.&#x20;

Sua sintaxe e a seguinte:

```
grep [OPCOES] PADRAO [ARQUIVO]
```

`--color` - Descarta os itens correspondentes com determinadas cores.&#x20;

`-c` - Fornece uma contagem de quantas linhas correspondem ao padrão.&#x20;

`-n` - Exibi números de linhas originais, todas as linhas e seus números de linhas.&#x20;

`-v` - Inverte a correspondência, produzindo todas as linhas que não contem o padrão.

`-i` - Ignora as distinções de maiúsculas e minusculas.&#x20;

`-w` - Retorna apenas linhas que contem correspondências que formam palavras inteira.&#x20;

`-E` - Pode ser usada para executar pesquisas com expressões regulares estendidas , expressões regulares essencialmente mais poderosas.
