---
description: >-
  Vamos utilizar os Provisioners para executar ações após a máquina ter sido
  criada pelo Provider
---

# Utilizando Provisioners

Iremos utilizar o provisioner `shell` para instalar o `nginx` na máquina ubuntu.

```bash
vim Vagrantfie
```

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "private_network", ip: "10.10.10.11"
  config.vm.provision "shell", inline: "sudo apt update && sudo apt install nginx -y"
end
```

Vamos construir nosso ambiente e verificar se o `nginx` foi instalado com sucesso

```bash
vagrant up
curl 10.10.10.11
```

Podemos também verificar diretamente no navegador digitando o endereço do servidor

```html
http://10.10.10.11
```

Vamos destruir nosso ambiente novamente.

```bash
vagrant destroy -f
```

{% hint style="info" %}
Podemos alterar a maneira na qual nosso script é chamado, uma das maneiras é declarando o script no início do arquivo, e novamente verificar se o nginx foi instalado corretamente.
{% endhint %}

```bash
vim Vagrantfie
```

```ruby
$script = <<-EOF
sudo apt update
sudo apt install nginx -y
EOF

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "private_network", ip: "10.10.10.11"
  config.vm.provision "shell", inline: $script
end
```

Vamos destruir nosso ambiente novamente.

```bash
vagrant destroy -f
```
