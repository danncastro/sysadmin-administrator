---
description: >-
  Vamos editar o Vagrantfile para definir o endereço IP e as configurações das
  interfaces de rede através do parâmetro vm.network
---

# Configurando Interfaces de Rede

```bash
vim Vagrantfile
```

```ruby
Vagrant.configure("2") do |config|
  config.vm.define "server1" do |server1|
    server1.vm.box = "ubuntu/bionic64"
    server1.vm.network "private_network", ip: "10.10.10.11"
  end
  config.vm.define "server2" do |server2|
    server2.vm.box = "centos/7"
    server2.vm.network "private_network", ip: "10.10.10.12"
  end
end
```

Vamos construir o ambiente e verificar o endereço IP das máquinas

```bash
vagrant up
vagrant ssh server1 -c "ip -c a show enp0s8"
vagrant ssh server2 -c "ip -c a show eth1"
```

Após isto, vamos destruir novamente nosso ambiente

```bash
vagrant destroy -f
```
