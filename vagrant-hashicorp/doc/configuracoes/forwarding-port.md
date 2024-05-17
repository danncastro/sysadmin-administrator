---
description: >-
  A configuração de porta encaminhada espera dois parâmetros, a porta do
  convidado e a porta do host.
---

# Forwarding Port

&#x20;**Exemplo:**

```ruby
Vagrant.configure("2") do |config|
  config.vm.network "forwarded_port", guest: 80, host: 8080
end
```

Isso permitirá acessar a porta 80 no guest por meio da porta 8080 no host.

Para a maioria dos provedores, as **Forwarding Port** por padrão são vinculadas a todas as interfaces. Isso significa que outros dispositivos em sua rede podem acessar as portas encaminhadas. Também é possível restringir o acesso, utilizando - se das configurações de **guest\_ip** e **host\_ip**.

***
