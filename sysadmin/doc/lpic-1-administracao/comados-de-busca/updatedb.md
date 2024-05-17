---
description: Utilizado para criação e atualização de bando de dados.
---

# updatedb

Este comando varre todo o sistema gerando uma listagem completa que por sua vez e copiada para o banco de dados.&#x20;

Dependendo do tamanho do sistema, pode-se agendar, via `cron`, a execução do `updatedb` com a frequência que for mais conveniente.&#x20;

> Horas, minutos ...etc.

{% hint style="info" %}
`updatedb.conf` não é um arquivo de configuração, mas apenas um meio de facilitar o uso do comando `updatedb` de forma que não precisamos passar os valores do arquivo `updatedb.conf` para a linha de comando.
{% endhint %}

> Usuários regulares não podem atualizar o arquivo de banco de dados.&#x20;

Opções mais utilizadas no comando updatedb.&#x20;

`-prunefs` - Grava sistemas de arquivos digitados na variável `PRUNEFS`.&#x20;

> Essa opção sobrescreve os valores passados para PRUNEFS em: `/etc/updatedb.conf`

`-f` - Adiciona valores (separados por espaços em branco) para a variável `PRUNEFS`.&#x20;

> Também pode ser digitado como: -add-prunefs.

Por exemplo:&#x20;

```bash
-n ou -add-prunefs Nomes_de_sistemas_de_arquivos)
```

`-prunenames` - Grava nomes digitados na variável `PRUNENAMES`.&#x20;

> Essa opção sobrescreve os valores passados para `PRUNENAMES` em. `/etc/updatedb.conf`

&#x20;`-n` - Adiciona valores (separados por espaços em branco) para a variável `PRUNENAMES`.&#x20;

> Também pode ser digitado como: -add-prunenames.

Por exemplo:&#x20;

```bash
-n ou -add-prunenames Digite_alguns_nomes_aqui
```

`-prunepaths` - Grava caminhos digitados na variável `PRUNEPATHS`.&#x20;

> Essa opção sobrescreve os valores passados para `PRUNEPATHS` em: `/etc/updatedb.conf`

`-e` - Adiciona valores (separados por espaços em branco) para a variável `PRUNEPATHS`.&#x20;

> Também pode ser digitado como: `-add-prunepaths`

Por exemplo:&#x20;

```bash
-e ou -add-prunepaths Digite_caminhos_de_arquivos
```

`-U`  - Armazena na base de dados apenas os caminhos passados para -U.&#x20;

Por padrão todo sistema de arquivo e passado para a base de dados do updatedb.&#x20;

> Também pode ser digitado como: -database-root&#x20;

• Por exemplo:&#x20;

```bash
-U ou -database-root Digite_caminhos_de_arquivos
```

`-o` - Grava em arquivo.db o conteúdo da base de dados.&#x20;

> Também pode ser digitado como: -output

&#x20;Por exemplo:

```bash
-o ou -output arquivo.db
```
