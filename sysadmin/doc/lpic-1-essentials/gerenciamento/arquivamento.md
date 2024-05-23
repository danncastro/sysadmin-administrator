---
description: >-
  Combina vários arquivos em um, o que elimina a sobrecarga em arquivos
  individuais e facilita a transmissão dos arquivos.
---

# Arquivamento

Se você tiver vários arquivos para enviar a alguém, poderá optar por compactar cada um individualmente. Você teria uma quantidade menor de dados no total do que se enviasse arquivos descompactados, no entanto, ainda teria que lidar com muitos arquivos ao mesmo tempo.&#x20;

O arquivamento é a solução para esse problema. É chamado o utilitário tradicional do UNIX para arquivar arquivos (.tar), que é uma forma curta do `Tape Archive`.&#x20;

O comando (tar) possui três modos úteis para se familiarizar:&#x20;

* **Criar:** Crie um novo arquivo com uma série de arquivos.&#x20;
* **Extrair:** Retire um ou mais arquivos de um arquivo morto.&#x20;
* **Lista**: Mostra o conteúdo do arquivo morto sem extrair.&#x20;

> A compressão (bzip2) pode ser usado em vez de substituindo (gzip).&#x20;

A opção `-j` para a opção `-z` e usar como extensão de arquivo.&#x20;

```bash
tar.bz2, .tbzou, .tbz2
```

O primeiro argumento zipfile e o nome do arquivo a ser criado, depois disso, uma lista de arquivos a serem adicionados.

***
