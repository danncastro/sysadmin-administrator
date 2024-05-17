---
description: Comando utilizado para navegar entre diretórios do sistema.
---

# cd (Change Directory)

### Ponto único

`.` - Independente do diretório em que o usuário esteja, o ponto sempre representa o diretório atual.

### Pontos Duplos

`..` - O caractere dois pontos representa um nível acima do diretório atual. Caracteres de ponto duplo sempre representam um diretório mais alto em relação ao diretório atual.&#x20;

{% hint style="info" %}
As vezes chamado de diretório pai.
{% endhint %}

&#x20;Por exemplo: Para mover do diretório Art de volta para o diretório School:

```bash
/home/sysadmin/Documents/School/Art$ cd ..
```

O ponto duplo também pode ser usado em caminhos mais longos. &#x20;

Por exemplo: O caminho relativo a seguir pode ser usado para mover do diretório School para o diretório Downloads:&#x20;

```bash
/home/sysadmin/Documents/School$ cd ../../Downloads
```

### Caminhos absolutos&#x20;

Caminhos absolutos permitem ao usuário especificar a localização exata de um diretório

```bash
/home/sysadmin/Documents$ cd /home/sysadmin
```

> Quando o caminho que é fornecido como argumento para o comando `cd` começa com a barra `/`, esse caminho é chamado de "caminho absoluto".&#x20;

Caminhos absolutos são sempre caminhos completos do diretório raiz para um subdiretório ou arquivo.

### Caminhos relativos&#x20;

Os caminhos relativos começam no diretório atual. Um caminho relativo fornece instruções para um arquivo em relação à localização atual no sistema de arquivos.&#x20;

> Eles não começam com o caractere `/`

Em vez disso, eles começam com o nome de um diretório. Mais especificamente, os caminhos relativos começam com o nome de um diretório contido no diretório atual.

```bash
/home/sysadmin/Documents$ cd Shool/Art
```

&#x20;(Com nomes de caminho relativos, você fornece **"instruções"** de onde deseja ir do diretório atual.
