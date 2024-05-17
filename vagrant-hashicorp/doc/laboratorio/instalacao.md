---
description: >-
  Para instalar o vagrant devemos acessar a página oficial de downloads e buscar
  o pacote referente ao seu sistema operacional.
---

# Instalação

```bash
cd /tmp
curl https://releases.hashicorp.com/vagrant/2.2.7/vagrant_2.2.7_x86_64.deb -o vagrant.deb
$ sudo dpkg -i vagrant.deb
```

Podemos executar o comando _**`vagrant --version`**_ para verificar se o vagrant foi instalado corretamente.

```bash
vagrant --version
```
