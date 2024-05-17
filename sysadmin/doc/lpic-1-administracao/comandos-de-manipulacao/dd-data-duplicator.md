---
description: Utilitário para copiar arquivos ou partições inteiras no nível de bit.
---

# dd (Data Duplicator)

```
dd  [opções] operando
```

{% hint style="info" %}
Este comando possui vários recursos uteis, incluindo: **"Pode ser usado para clonar ou excluir (limpar) discos ou partições inteiros."**
{% endhint %}

Pode ser usado para copiar dados brutos para dispositivos removíveis, como unidade USB e CD ROMs.&#x20;

Pode fazer backup e restaurar o **MBR (Master Boot Record).**&#x20;

Pode ser usado para criar um arquivo de tamanho especifico preenchido com zeros binários, que pode ser usado como arquivo de troca (Memoria virtual).

O comando (dd) usa argumentos especiais para especificar como ele funcionara. Exemplos mais usados: `Argumento: Descrição:`

Este exemplo lê do arquivo `/dev/zero` , um arquivo especial que contem um numero ilimitado de zeros.

```bash
dd if=/dev/zero of=/tmp/swapex bs=1M count=50
```

> if - Arquivo de entrada a ser lido;

> of - Arquivo de saída a ser gravado;

> bs - Tamanho do bloco a ser usado;

Este exemplo usa um tamanho de bloco de 1 megabyte. Por padrão o valor é considerado em bytes. Use os seguintes sufixos para especificar outras unidades&#x20;

* `bs=1K` - kilobytes
* `bs=1M` - megabytes
* `bs=1G` - gigabytes&#x20;
* `bs=1T` - terabytes.

> count Contagem - Numero de blocos a serem lidos no arquivo de entrada;

Este exemplo lê 50 blocos.&#x20;

> Não e necessário especificar nenhum tamanho ou contagem de bloco ao copiar em dispositivos inteiros.&#x20;

Por exemplo: Para clonar de um disco rígido `/dev/sda` para outro `/dev/sdb`.&#x20;

```bash
dd if=/dev/sda of=/dev/sdb
```
