---
description: Utilizado para  procurar por arquivos na arvore de diretórios.
---

# find

O comando `find` iniciara a pesquisa no diretório especificado e pesquisara recursivamente todos os subdiretorios.

> Isto é, ele tenta localizar o que solicitamos dentro do local que indicamos checando os subdiretórios tambem.

Por exemplo: Para procurar arquivos começando no diretorio inicial que contem o nome bash.

```bash
find ~ -name  "*bash*"
```

> Este comando é muito flexível, permite pesquisar com uma variedade de opções como nome do arquivo, tamanho, data, tipo e permissão.

Este comando pesquisa o sistema de arquivos ativo, em vez de um banco de dados estático.

A sintaxe do comando e a seguinte:

```bash
find [CAMINHO] [OPCOES] [NOMES_DO_ARQUIVO].
```
