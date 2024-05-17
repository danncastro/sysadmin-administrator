---
description: Para definir nossa máquina virtual utilizaremos o Vagrantfile
---

# Definindo as Máquinas Virtuais

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus   = "2"
  end
end
```

No exemplo acima estamos definindo uma infraestrutura de apenas uma máquina com a box do _**Ubuntu Bionic 64bits**_, a máquina possuirá _**1024 MiB**_ de _**RAM**_ e _**2 vCPUs**_.

{% hint style="info" %}
Toda estrutura do _**Vagrantfile**_ começa informando a _**versão (Major Version)**_ que irá utilizar do Vagrant e termina com a palavra end.
{% endhint %}

Como nosso vagrant está na _**versão 2.2.7**_, a major version é a 2, então o arquivo começará com:

```ruby
Vagrant.configure("2") do |config|
```

E como segue a estrutura do `ruby`, terminará com um **end**.

O próximo passo é informar qual a box que iremos utilizar nessa instância, nesse caso utilizaremos uma imagem chamada **ubuntu/bionic64**

```ruby
config.vm.box = "ubuntu/bionic64"
```

Por último criamos uma infraestrutura onde informamos qual o provedor da nossa instância e suas configurações como **cpu, memória, hostname, disco, etc**...

```ruby
config.vm.provider "virtualbox" do |vb|
```
