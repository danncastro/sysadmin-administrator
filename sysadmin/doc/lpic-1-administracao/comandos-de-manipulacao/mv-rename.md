---
description: >-
  O comando mv não é usado apenas para mover um arquivo, mas também para
  renomear um arquivo.
---

# mv (Rename)

Se o destino do comando `mv` for um diretório, o arquivo será movido para o diretório especificado. O nome do arquivo muda apenas se um nome de arquivo de destino também for especificado.

Exemplo:&#x20;

```bash
sysadmin:localhost:$ mv exemplo.txt Videos/novo_exemplo.txt
```

Se um diretório de destino não for especificado, o arquivo será renomeado usando o nome do arquivo de destino e permanecerá no diretório de origem.

Por exemplo: Os seguintes comandos renomeiam o arquivo  `"newexample.txt"` para `"myfile.txt"`&#x20;

```bash
sysadmin@localhost:/Videos$ mv newexemple.txt myfile.txt
```
