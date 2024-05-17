---
description: Receberá o comando de join do cluster e um script para configurar o master
---

# worker.sh & master.sh

```bash
touch worker.sh
vim master.sh
```

```bash
#!/bin/bash
sudo docker swarm init --advertise-addr=10.10.10.100
sudo docker swarm join-token worker | grep docker > /vagrant/worker.sh
```

Após tudo isto basta executar o comando `vagrant up` que todo o ambiente estará disponível em questão de minutos.

Podemos verificar estado do cluster através do comando

```bash
vagrant ssh master -c "docker node ls"
```
