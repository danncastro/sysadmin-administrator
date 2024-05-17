---
description: >-
  Este comando pesquisa um banco de dados de todos os arquivos e diretórios que
  estavam no sistema quando o banco de dados foi criado.
---

# locate

O banco de dados utilizado pelo comando `locate` fica localizado em

```bash
/var/lib/mlocate/mlocate.db
```

O comando `locate` na verdade e um link logico que aponta para o comando `mlocate`.&#x20;

Algumas das opções do comando:&#x20;

`-c` - Exibe quantos arquivos correspondem ao digitado.&#x20;

`-b` - Procura pelo nome do arquivo literalmente digitado.&#x20;

> Também pode ser digitado como: `-basename`

Por exemplo:&#x20;

```bash
locate -b tree
```

O locate ira procurar por arquivos apenas com o nome “tree”, não ira buscar por “tree.txt” ou arquivotree.txt” ...etc.&#x20;

Esse caractere limita a saída a nomes de arquivos que correspondem exatamente ao termo.&#x20;

`-i` - Não faz diferença entre letras maiúsculas e minúsculas.

> Também pode ser digitado como: -ignore-case.

`-s` - Exibe estatísticas, como localização da base de dados, total de diretórios e arquivos indexados na base ...etc.&#x20;

> Também pode ser digitado como: `-statistics`

Existem varias implementações do locate:&#x20;

{% hint style="info" %}
A original encontrada nas findutils da GNU, e `mlocate`.
{% endhint %}
