---
description: >-
  Modifique agora o arquivo para adicionarmos uma segunda instância para nossa
  infraestrutura
---

# Construindo Múltiplas Instâncias

```bash
vim Vagrantfile
```

```ruby
Vagrant.configure("2") do |config|
  config.vm.define "server1" do |server1|
    server1.vm.box = "ubuntu/bionic64"
  end
  config.vm.define "server2" do |server2|
    server2.vm.box = "centos/7"
  end
end
```

Vamos construir nossa infraestrutura novamente e verificar os status da mesma

```bash
vagrant up
vagrant status
```

Para acessar cada máquina podemos utilizar o comando

```bash
vagrant ssh <machine_name>
```

```bash
vagrant ssh server1
exit
```

Podemos também verificar o sistema operacional através do comando

```bash
cat /etc/*release.
exit
```

Podemos também executar um comando diretamente através do parâmetro _**`-c`**_ no _**`vagrant ssh`**_

```bash
vagrant ssh server1 -c "cat /etc/*release"
vagrant ssh server2 -c "cat /etc/*release"
```

Vamos destruir nosso ambiente.

```bash
vagrant destroy -f
```

{% hint style="info" %}
O parâmetro _**-f**_ força o comando executado sem solicitar confirmação.
{% endhint %}
