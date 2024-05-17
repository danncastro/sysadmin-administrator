## InSpec 
- É um framework gratuito e Open Source para teste e auditoria de aplicações e infraestrutura criado pela ***Chef*** para atender a demanda de ***Compliance-as-a-Code.***
- O ***InSpec*** torna-se extremamente poderoso por não necessitar de um agent instalado para efetuar os testes, por possuir uma linguagem declarativa de fácil entendimento e escrita, por funcionar em qualquer sistema operacional ***(que aceite conexões SSH)*** e por ter sua documentação extremamente detalhada.

---
#### Vagrantfile para o InSpec
Vamos criar um diretório para armazenar o conteúdo do Vagrantfile e popula-lo com as configurações para subir o ambiente.

    ~~~bash
    mkdir ~/inspec
    cd ~/inspec
    vim Vagrantfile
    ~~~

    ~~~Vagrantfile
    # -*- mode: ruby -*-
    # vi: set ft=ruby  :

    Vagrant.configure("2") do |config|

        config.vm.box_check_update = false
        config.vm.boot_timeout = 600
        config.vm.define "inspec" do |machine|
            machine.vm.box = "ubuntu/bionic64"
            machine.vm.hostname = "inspec.caiodelgado.example"
            machine.vm.network "private_network", ip: "10.10.10.11"
            machine.vm.provider "virtualbox" do |vb|
            vb.name = "inspec"
            vb.memory = "1024"
            vb.cpus = "1" 
            vb.customize ["modifyvm", :id, "--groups", "/iac"]
            end
        end
    end
    ~~~

    ~~~bash
    vagrant up 
    ~~~

- Adicione a entrada do inspec no arquivo hosts para que o acesso ao mesmo fique mais fáci

    ~~~bash
    sudo sh -c "echo '10.10.10.11 inspec.caiodelgado.example' >> /etc/hosts"
    ~~~

- Vamos acessar o servidor para instalar o inspec.

    ~~~bash
    cd ~/inspec
    vagrant ssh
    ~~~

- Agora que estamos conectados no servidor podemos acessar a página de Downloads para instalar o InSpec de acordo com seu Sistema Operacional.

    ~~~bash
    sudo su -
    cd /tmp
    curl https://packages.chef.io/files/stable/inspec/4.18.104/ubuntu/18.04/inspec_4.18.104-1_amd64.deb -o inspec.deb
    sudo dpkg -i inspec.deb
    ~~~

- Execute o comando ***inspec --version*** para garantir que a instalação foi efetuada com sucesso.
- Uma vez instalado podemos seguir  com o entendimento da ferramenta.

---
#### InSpec Shell
- O primeiro recurso que precisamos entender é o ***InSpec Shell.***
- Vamos executar o ***inspec shell.***

    ~~~bash
    inspec shell
    ~~~

- Será exibido uma tela em sua primeira execução para aceitar a licença do produto, ***digite yes.***
- A licença está disponível para leitura no .***website da chef.***
- Após a abertura do ***inspec shell.*** recebemos uma tela com informações do nosso sistema operacional juntamente a uma mensagem de boas vindas ao inspec shell.
- Nossa ***PS1*** será modificada para ***inspec>*** informando que estamos dentro do shell do inspec, podemos utilizar o comando ***help*** para verificar os comandos possíveis.
- O ***InSpec*** trabalha com resources, para ver quais resources estão disponíveis podemos utilizar o comando 
    
    ~~~bash
    help resources
    ~~~

- Podemos também verificar o help de um determinado recurso através do comando 
    
    ~~~bash
    help <resource>
    ~~~

- O comando ***help < resource >*** é bastante interessante, uma vez que ele mostra um exemplo de definição de teste.
- Para utilizar este recurso, primieiramente precisaremos definir o alvo deste recurso, para fazer esta declaração utilizamos o comando ***< recurso >('< alvo >').*** Vamos criar nosso primeiro recurso para interagir por exemplo com o arquivo ***\etc\hosts.***

    ~~~bash
    inspec> file('/etc/hosts')
    ~~~

- Uma vez criado nosso recurso, podemos visualizar as subrotinas dele chamando ***< recurso >('< alvo >').methods .***
- ***ATENÇÃO:*** Para sair de uma navegação do ***.methods*** ou qualquer outra do inspec shell, pressione a ***tecla q*** , caso seja pressionado algum outro signal ***(ex: SIGINT < ctrl >+< c >)*** o terminal ficará travado. ***NUNCA FAÇA ISSO***, ou será necessário finalizar o inspec shell e iniciar uma nova sessão. Para navegar é possível utilizar as setas direcionais.

    ~~~bash
    inspec> file('/etc/hosts/').methods
    ~~~

- Pressione ***q*** para sair da listagem dos métodos e vamos fazer algumas verificações.

    ~~~bash
    inspec> file('/etc/hosts').exist?
    inspec> file('/etc/hosts').content
    inspec> file('/etc/hosts').mode
    ~~~

- Podemos também fazer testes por exemplo através do recurso Package e verificar informações de um pacote.

    ~~~bash
    inspec> package('vim').installed?
    inspec> package('vim').version
    inspec> package('vim').info
    ~~~

---
#### Entendendo Comparadores
- Antes de escrever nossos testes, primeiramente precisamos entender os comparadores. 
- Podemos lista-los através do comando ***help matchers*** no inspec shell.
- Basicamente os matchers ***(comparadores)*** são:

    |Matcher |Uso                                                 |
    |:-------|:---------------------------------------------------|
    |be	     |Comparação de valores numéricos                     |
    |eq	     |Igualdade entre dois valores                        |
    |cmp     |Igual ao eq porém menos restritivo                  |
    |include |Verifica se o valor está incluso em uma lista       |
    |match	 |Verifica um texto utilizando uma RegEX              |

- O matcher ***cmp*** consegue comparar, por exemplo, valores binários com valores hexadecimais ou valores octais por exemplo, ele entende que um valor ***X*** equivale a um valor ***Y*** em outra notação

---
#### Entendendo Controles
- O ***InSpec*** utiliza de ***controls (controles)*** para expressar as expectativas com relação a um estado de um recurso, podendo ser propriedades, comparadores, condições, etc...
- Vamos descrever um controle no ***inspec shell*** para verificar se um arquivo existe.

    ~~~inspec
    describe file('/etc/resolv.conf') do
        it  { should exist }
    end
    ~~~

- Será exibido um relatório com os controles realizados. Podemos também descrever vários controles em um único recurso.

    ~~~inspec
    describe file('/etc/resolv.conf') do
        it  { should exist }
        it  { should be_file }
        it  { should be_owned_by 'systemd-resolve' }
        its('mode') { should eq '0644' }
    end
    ~~~

- Perceba que o teste ***its('mode') { should eq '0644' }*** falhou pois utilizamos o ***eq*** o qual realiza um teste literal do alvo. Neste caso podemos utilizar o ***cmp*** que irá igualar as unidades octal e decimal passando assim o teste.

    ~~~inspec
    describe file('/etc/resolv.conf') do
        it  { should exist }
        it  { should be_file }
        it  { should be_owned_by 'systemd-resolve' }
        its('mode') { should cmp '0644' }
    end
    ~~~

- Após a execução digite ***exit*** para sair do inspec shell.

---
#### Executando o inspec shell remotamente
- Abra um novo terminal e ligue a máquina vault

    ~~~bash
    cd ~/vault-101
    vagrant up
    ~~~

- Agora que temos a máquina disponível, podemos executar o ***inspec shell*** da máquina inspec para acessar a máquina vault.
- Para isto podemos acessar utilizando uma chave de acesso ou uma senha.

    ~~~inspec
    inspec shell -t ssh://<usuario>@<host> --password <senha>
    inspec shell -t ssh://<usuario>@<host> -i <private-key>
    ~~~

- Podemos omitir o parâmetro ***--password*** e digitar o mesmo após a solicitação de maneira segura.
- Primeiramente vamos criar um par de chaves para utilização da máquina inspec.

    ~~~bash
    $ ssh-keygen -m PEM -f ~/.ssh/id_rsa
    <ENTER>
    <ENTER>
    ~~~

- Agora vamos copiar o conteúdo da chave publica gerada pela máquina inspec. E adiciona-la a máquina vault.
- ***ATENÇÃO:*** Altere os valores de acordo com a chave gerada em sua máquina
- #### ***Na máquina inspec:***

    ~~~bash
    cat ~/.ssh/id_rsa.pub
    ~~~

- Copie o conteúdo da chave pública
- #### ***Na máquina vault***
    ~~~bash
    sudo sh -c "echo 'conteudo da chave publica' >> /root/.ssh/authorized_keys 
    ~~~

- Agora que a chave da máquina ***inspec*** está inserida na máquina vault podemos acessar a mesma através do inspec shell
- #### ***Na máquina inspec:***

    ~~~inspec
    inspec shell -t ssh://root@vault.caiodelgado.example -i ~/.ssh/id_rsa
    ~~~

- Como saber se estou de fato conectado na máquina vault através do inspec shell? simples, podemos executar diversos comandos como por exemplo

    ~~~inspec
    inspec> sys_info.hostname
    inspec> interface('enp0s8').ipv4_addresses
    ~~~

- Vamos executar um novo teste.
    
    ~~~inspec
    describe service('vault') do
        it { should be_enabled }
        it { should be_running }
    end
    ~~~

- Através dos testes acima, conseguimos verificar que um serviço está habilitado e sendo executado, conseguimos ir mais a fundo nos testes verificando inclusive se uma aplicação está em estado ***listening*** por exemplo.
- Sabemos que o servidor vault possui dois serviços, um do ***mysqld*** escutando na ***porta 3306*** e um do ***vault*** escutando na ***porta 8200***
- Vamos fazer um teste para o ***mysqld*** e um teste para o ***vault.***
- #### ***mysqld***

    ~~~inspec
    describe port('3306') do
        it { should be_listening }
        its('processes') { should include 'mysqld' }
    end
    ~~~

- #### ***vault***

    ~~~inspec
    describe port('8200') do
        it { should be_listening }
        its('processes') { should include 'vault' }
    end
    ~~~

- Após isto, podemos fechar o inspec shell digitando ***exit.***

---
#### Listando requerimentos os testes
- Agora que entendemos como os testes funcionam, precisamos escrever os testes para nosso ambiente. Para isto precisamos definir os requerimentos para os testes.
- Os dados que eu particularmente gosto de levar em conta para descrever os testes são:
    - ***Estrutura -*** Quais programas devem ser testados?
    - ***Dados -*** Existe algum arquivo que seu conteúdo deve ser persistente?
    - ***Funcionalidade --*** Existe alguma porta para ser testada? Acesso a internet?
    - ***Plataforma -*** É preciso verificar qual o Sistema Operacional?
    - ***Segurança -*** Hardening? CVS? LGPD? etc...

- Vamos descrever os requerimentos para a máquina vault
    - ***Pacotes Instalados***
        - /usr/bin/vault
    - ***Serviços em Execução***
        - vault
        - mysqld
    - ***Arquivos de Configuração***
        - /etc/vaul.d/config.hcl
    - ***Portas***
        - 8200
        - 3600
- Vamos armazenar os arquvios de testes no diretório ***/vagrant*** da máquina ***inspec***
- O diretório ***/vagrant*** é sincronizado com o diretório do ***Vagrantfile***, sendo assim conseguirei compartilhar de maneira íntegra o arquivo no github bem como rodar outros laboratórios tendo o arquivo disponível após uma possível destruição da máquina vagrant.
- #### ***Na máquina inspec:***

    ~~~bash
    mkdir -p /vagrant/inspec-profiles/
    cd /vagrant/inspec-profiles/
    ~~~

#### Profiles
- :***Profiles:*** são utilizados pelo :***InSpec:*** para organizar multiplos controles em um artefato reutilizavel e versionável.
- Vamos criar nosso primeiro profile:

    ~~~bash
    cd /vagrant/inspec-profiles/
    inspec init profile vault
    ~~~

- Este comando irá criar toda a estrutura de diretórios, por ora iremos trabalhar apenas com o arquivo de controle.
- Vamos remover o arquivo: ***controls/example.rb .:***

    ~~~inspec
    rm /vagrant/inspec-profiles/vault/controls/example.rb
    ~~~

- Agora iremos criar um arquivo na pasta ***controls*** chamado ***vault.rb***
- É importante que o arquivo tenha a extensão ***.rb*** uma vez que seu código é baseado em ***ruby***, por padrão o inspec varre o diretório ***controls*** dentro de um determinado ***profile*** e executa todos os ***controles .rb***
- Antes de criar nosso arquivo vault precisamos entender que o ***InSpec*** trabalha com parâmetros de ***impacto (impact)*** baseados no ***CVSS 3.1 (Common Vulnerability Scoring System)*** o que é um framework de pontuação de vulnerabilidades.
- Em resumo, os valores possíveis são:
    - 0.0 até < 0.01 ou none - Sem Impacto, Informações
    - 0.1 até < 0.4 ou low - Baixo Impacto
    - 0.4 até < 0.7 ou medium - Médio Impacto
    - 0.7 até < 0.8 ou high - Alto Impacto
    - 0.9 até < 1.0 ou critical - Impacto Crítico
- Os impactos tratam como será dado o ***return code*** do teste, sendo assim falhando ou não o teste geral, um ***impacto critical*** falha o teste, mesmo que tenhamos ***1000 testes*** none passando com sucesso, então é muito importante definir os niveis através do CVSS 3.1
- Vamos criar gora nosso ***control de teste*** para o vault de acordo com os requerimentos definidos.

    ~~~bash
    vim /vagrant/inspec-profiles/vault/controls/vault.rb
    ~~~

    ~~~inspec
    title "Tests for Vault application"

    control "Vault Binary" do
        impact "high"
        title "Vault Binary"
        desc "Test if Binary of Vault its installed and working"
        describe file("/usr/local/bin/vault") do
            it { should exist }
            it { should be_file }
        end
        describe command("vault") do
            it { should exist } 
        end
        describe command("vault --version") do
            its("stdout") { should cmp > "Vault v1" }
        end 
    end

    control "Mysql Service" do 
        impact "critical"
        title "Mysql Service"
        desc "Test if Mysql binary is present, if the server is running and listening"
        describe service("mysqld") do
            it { should be_enabled }
            it { should be_running }
        end
        describe package("mariadb-server") do
            it { should be_installed }
            its("version") { should cmp > "1:10" }
        end
        describe port("3306") do
            it { should be_listening }
            its("processes") { should include "mysqld" }
        end 
    end

    control "Vault Server" do
        impact "critical"
        title "Vault Server"
        desc "Test if vault server is installed, running and listening, and its config file content is correct"
        describe service("vault") do
            it { should be_enabled }
            it { should be_running }
        end
        describe port("8200") do
            it { should be_listening }
            its("processes") { should include "vault" }
        end
        describe file("/etc/vault.d/config.hcl") do 
            it { should be_file }
            it { should be_owned_by "vault" }  
            its("content") { should include 'storage "mysql"' }
            its("content") { should include 'username = "vaultuser"' }
            its("content") { should include 'database = "vault"' }
            its("content") { should include 'listener "tcp"' }
            its("content") { should include '10.10.10.10:8200' }
        end
    end
    ~~~

- Podemos verificar a sintax através do comando ***inspec check profile < path >***

    ~~~inspec
    inspec check /vagrant/inspec-profiles/vault
    ~~~

- Uma vez construido e funcional nosso teste, podemos executar através do comando ***inspec exec***

    ~~~inspec
    inspec exec /vagrant/inspec-profiles/vault -t ssh://root@vault.caiodelgado.example -i ~/.ssh/id_rsa
    ~~~

- Os testes com sucesso são apresentados em ***verde*** e os testes com falha são apresentados em ***vermelho.***
- Irei parar o serviço do .***vault.*** no .***vault server.*** para fins de exemplo e rodar novamente o comando.

#### Supermarket
- O InSpec também dispõe de um repositório de ***profiles*** chamado ***supermarket.*** Podemos executar os testes diretamente do supermarket bem como listar os testes disponíveis.
- Liste os profiles disponíveis no supermarket e exiba informações sobre um profile.

    ~~~inspec
    inspec supermarket profiles
    inspec supermarket info dev-sec/linux-baseline
    ~~~

- Os profiles ***dev-sec*** fazem parte de uma iniciativa de automação de hardening de servidores, basicamente definem testes bases para serem utilizados em diversas situações.

- Para rodar um profile do supermarket podemos executar de duas maneiras

    ~~~inspec
    inspec supermarket exec <profile_name>
    inspec exec supermarket://<profile_name>
    ~~~

- O benefício de se utilizar o comando ***inspec exec supermarket://< profile >*** é que o output do comando é exibido em cores, facilitando sua leitura, podemos também utilizar o ***parâmetro -t*** para apontar o ***target*** do teste.
- Execute o profile  ***dev-sec/linux-baseline*** remotamente na máquina vault.

    ~~~inspec
    inspec exec supermarket://dev-sec/linux-baseline -t ssh://root@vault.caiodelgado.example -i ~/.ssh/i d_rsa
    ~~~

- Podemos verificar através da execução do profile ***dev-sec/linux-baseline*** que a box do vagrant possui diversas falhas de segurança, uma vez que não existe o hardening, por este motivo citei no meu post ***vagrant-101*** que não recomendo a utilização de box prontas para ambientes que não sejam de desenvolvimento e estudo.