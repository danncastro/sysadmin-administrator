---
description: >-
  O Vagrant automaticamente compartilha uma pasta entre o host e o guest (Synced
  Folder)
---

# Synced Folder

Por padrão, é compartilhada a pasta onde se encontra o Vagrantfile. Na máquina guest, podemos acessar a pasta pelo caminho /vagrant

A pasta compartilhada pode ser reconfigurada no Vagrantfile:

```ruby
config.vm.synced_folder "src/", "/public"
```

**Exemplo:**

```ruby
config.vm.synced_foder "./configs", "/configs"
config.vm.synced_folder ".", "/vagrant", disable:true
```

***
