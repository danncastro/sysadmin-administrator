---
description: >-
  O Provisionador (provisioner) é o responsável pelas tarefas a serem executadas
  de forma automatizada, como por exemplo a instalação de pacotes e a
  configuração do sistema
---

# Privisioners

O Vagrant oferece suporte a diversos provisioners como por exemplo _**Ansible, Chef, Puppet, Shell, File, etc...**_

{% hint style="info" %}
Provisionar significa fornecer a **rede, CPU, memória, espaço**, mas também o **sistema operacional** e **pacotes**, além da implantação em si.&#x20;
{% endhint %}

Tudo o que for preciso para **rodar/executar o serviço** de forma automatiza

**Exemplo**: Para usar o Shell Provisionar, basta definir um script com os passos de instalação:

```ruby
Vagrant.configure("2") do |config|
config.vm.provision "shell", path: "script.sh"
end
```

Os comandos do Shell Provisioner também podem ser usados de maneira inline ou remoto:

```ruby
$script = <<-SCRIPT
  echo Instalando MySQL
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: $script
end
```

```ruby
Vagrant.configure("2") do |config|
  config.vm.provision "shell", path: "https://seu-servidor/script.sh"
end
```

```ruby
config.vm.provision "shell", inline: "cat /configs/id_bionic_al.pub >> .ssh/authorized_keys"
```
