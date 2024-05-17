---
description: >-
  Podemos utilizar o comando vagrant init box para que seja criado o arquivo do
  Vagrantfile esse arquivo é criado com diversas opções já preenchidas, porém
  comentadas.
---

# Criando nossa primeira instância

{% hint style="info" %}
Para quem está começando a trabalhar com o vagrant, talvez seja a melhor opção, caso contrário podemos passar o parâmetro **`-m`**` ``ou`` `**`--minimal`** para remover todas as linhas comentadas e deixar somente o necessário.
{% endhint %}

Crie um diretório para armazenar os arquivos do nosso tutorial.

```bash
mkdir ~/vagrant/
cd ~/vagrant/
vagrant init -m ubuntu/bionic64
```

```bash
ssh-keygen -q -t rsa -f /vagrant/key -N ''
```

```
vagrant ssh instancia
vim .ssh/authorized_key
"Colar chave no final do arquivo"
```

Edite o arquivo para que fique igual a nosso exemplo

```bash
vim Vagrantfile
```

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus   = "2"
  end
end 
```

Para verificar se a sintaxe está correta, podemos utilizar o comando `validate`:

```bash
vagrant validate
```

Vamos construir o ambiente de acordo com o que se encontra parametrizado no _**Vagrantfile**_:

```bash
vagrant up
```

Agora que temos nosso ambiente disponível, podemos acessar o mesmo através do comando:

```bash
vagrant ssh
```

Conecte-se a máquina e desconecte-se em seguida

{% hint style="info" %}
Quando utilizamos o comando _**`vagrant ssh`**_ o que acontece **"por trás dos panos"** é simplesmente um comando SSH comum, onde a chave utilizada esta armazenada no diretório oculto _**.vagrant**_ localizado no mesmo diretório do Vagrantfile.
{% endhint %}

Podemos verificar a fundo os parâmetros e configurações utilizados pelo vagrant ssh

```bash
vagrant ssh-config
```

Para desligar a máquina podemos utilizar o comando

```bash
vagrant halt
```

E para destruir o ambiente podemos executar o comando

```bash
vagrant destroy -f
```
