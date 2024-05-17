---
description: >-
  Comando utilizado para compactar arquivos para ser compartilhados com
  utilizadores Windows.
---

# zip

Diferente dos outros compactadores como `gzip, bzip2` o comando `zip` compacta uma copia do arquivo original, fazendo com que o arquivo original permanece descompactado.

> Arquivos criados com o comando `zip` terminam com a extensão `.zip`

Não é necessário usar a extensão .zip para o nome de arquivo morto, no entanto, é útil para identificar o tipo de arquivo.&#x20;

> É considerado “Boas praticas” ao enviar um arquivo morto para outra pessoa.

&#x20;Sua sintaxe e a seguinte:&#x20;

```bash
zip [OPÇÕES] [zipfile [arquivo…]]
```

`-r` - Esta opção especifica a recursividade em diretórios.&#x20;

`-l` - Visualiza o conteúdo do arquivo `.zip`
