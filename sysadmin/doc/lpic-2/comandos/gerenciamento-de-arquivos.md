---
description: Gerenciamento de arquivos
---

# Gerenciamento de arquivos

### Buscando arquivos em apenas 2 níveis de subpastas

```bash
find /etc -maxdepth 2-name *.conf
```

***

### Buscando arquivos com 2GB ou mais

```bash
sudo find / -size +2G
```

***

### Buscar arquivos pelo tamanho

```bash
find /export -xdev -type f -size +50M | xargs du -sh
```

### Filtrar informações de um arquivo apenas pela 1° coluna

```bash
cut -d " " -f1
```

### Filtra em um arquivo palavras começadas **( ^ )** e terminadas **( $ )** com "computer"

```bash
cat american-english | grep -E "^computer$"
egrep ^computer$ american-english
```

### Validar as permissões de um diretorio

```bash
stat -c %a /diretorio
```
