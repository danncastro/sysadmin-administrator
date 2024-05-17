---
description: Private Network and Public Network
---

# Network

### **Private Network**

**DHCP:**

A maneira mais fácil de usar uma rede privada é permitir que o IP seja atribuído via DHCP.

```ruby
Vagrant.configure("2") do |config|
  config.vm.network "private_network", type: "dhcp"
end
```

Isso atribuirá automaticamente um endereço IP do espaço de endereço reservado. O endereço IP pode ser determinado usando **vagrant ssh**

{% hint style="info" %}
O SSH na máquina e usando a ferramenta de linha de comando apropriada para encontrar o IP, como **ifconfig** ou **ip addr show**.
{% endhint %}

**Static IP:**

Você também pode especificar um endereço IP estático para a máquina. Isso permite que você acesse a máquina gerenciada pelo Vagrant usando um IP estático conhecido. O Vagrantfile para um IP estático se parece com isso:

```ruby
Vagrant.configure("2") do |config|
  config.vm.network "private_network", ip: "192.168.50.4"
end
```

***

### **Public Network**

As redes públicas vagrant são menos privadas do que as redes privadas, e o significado exato varia de provedor para provedor , daí a definição ambígua. A ideia é que, embora as redes privadas nunca devam permitir o acesso do público em geral à sua máquina, as redes públicas podem.

**DHCP:**

```bash
Vagrant.configure("2") do |config|
  config.vm.network "public_network"
end
```

_**Usando a rota padrão atribuída por DHCP:**_

```bash
Vagrant.configure("2") do |config|
  config.vm.network "public_network",
    use_dhcp_assigned_default_route: true
end
```

**Static IP:**

Dependendo da sua configuração, você pode querer definir manualmente o IP da sua interface em ponte.&#x20;

{% hint style="info" %}
Para fazer isso, adicione uma cláusula **ip:** à definição de rede
{% endhint %}

```bash
config.vm.network "public_network", ip: "192.168.0.17"
```

_**Interface de rede padrão**_

Se mais de uma interface de rede estiver disponível na máquina host, o Vagrant solicitará que você escolha para qual interface a máquina virtual deve fazer a ponte.&#x20;

{% hint style="info" %}
Uma interface padrão pode ser especificada adicionando uma :bridge na definição de rede.
{% endhint %}

```bash
config.vm.network "public_network", bridge: "en1: Wi-Fi (AirPort)"
```

***
