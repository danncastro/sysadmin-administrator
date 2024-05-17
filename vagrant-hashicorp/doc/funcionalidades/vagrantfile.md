---
description: >-
  O Vagrantfile é o arquivo responsável por descrever nossa infraestrutura e
  subir a aplicação diretamente no Vagrant.
---

# Vagrantfile

O arquivo tem sua estrutura **HCL** porém é possível utilizar todos os recursos da linguagem Ruby para descrever o mesmo.

{% hint style="info" %}
É importante que o arquivo tenha o nome de _**Vagrantfile (case-sensitive)**_ ou o comando do vagrant não irá localiza-lo
{% endhint %}

Exemplo de configurações&#x20;

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.define "rabbitmq01" do |rabbitmq1|
    rabbitmq1.vm.hostname = "rabbitmq01"
    rabbitmq1.vm.network "public_network", bridge: "Intel(R) Dual Band Wireless-AC 8265"
    rabbitmq1.vm.provider :virtualbox do |vm|
      vm.cpus = 1
      vm.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vm.customize ["modifyvm", :id, "--memory", 512]
      vm.customize ["modifyvm", :id, "--name", "rabbitmq01"]
    end
    rabbitmq1.vm.provision "shell", inline: $iprabbitmq1
    rabbitmq1.vm.provision "shell", inline: $confignet
  end
end
```

***
