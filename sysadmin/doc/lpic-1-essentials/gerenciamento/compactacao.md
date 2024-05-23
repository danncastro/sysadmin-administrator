---
description: Reduz os arquivos removendo informações redundantes.
---

# Compactação

Os arquivos podem ser compactados individualmente ou vários arquivos podem ser combinados em um único arquivo e, posteriormente, compactados.&#x20;

{% hint style="info" %}
O último ainda é chamado de arquivamento.
{% endhint %}

Ao falar sobre compactação, existem dois tipos:&#x20;

* **Sem perdas:** Nenhuma informação é removida do arquivo. A compactação e descompactação de um arquivo deixa algo idêntico ao original.&#x20;
* **Com perdas:** As informações podem ser removidas do arquivo.  É compactado de forma que a descompactação de um arquivo resulte em um arquivo ligeiramente diferente do original.&#x20;

> Por exemplo: Uma imagem com dois tons de verde sutilmente diferentes pode ser reduzida ao tratar esses dois tons da mesma forma.&#x20;

Muitas vezes, o olho não consegue perceber a diferença de qualquer maneira.&#x20;

A maioria dos formatos de imagem, como: `GIF, PNG e JPEG` Implementa alguma forma de compactação com perdas.&#x20;

Os arquivos compactados podem ser restaurados para sua forma original usando o comando `gunzip` ou o comando `gzip` seguido da opção `–d`◦&#x20;

> Esse processo é chamado de descompressão

O comando `gzip` usa o algoritmo de compactação de dados **Lempel-Ziv**.&#x20;

Enquanto os utilitários `bzip` usam um algoritmo de compactação diferente chamado de classificação de blocos Burrows-Wheeler.&#x20;

Que pode compactar arquivos menores do que gzipar, que custa  um  tempo mais da CPU.

***
