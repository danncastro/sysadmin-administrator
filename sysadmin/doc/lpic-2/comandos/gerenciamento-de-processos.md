---
description: Gerenciamento de processos
---

# Gerenciamento de processos

### Lista os processos que estão em execução no bash atual

```bash
ps
```

### Lista todos os processos do sistema com informações completas

```bash
ps -ef
```

### Interrompe a execução de um processo

```bash
kill -STOP pid
```

### Retornar à execução do processo que foi interrompido anteriormente

```bash
kill -CONT pid
```

### Encerrar um processo de forma que ele possa realizar algumas tarefas antes de ser encerrado

É executado por padrão quando não indicamos nenhum sinal para o comando `kill`

```bash
kill -TERM pid
```

### Mata o processo em casos críticos, garantindo que o programa será encerrado imediatamente

```bash
kill -9 pid
killall -9 serviço
```

### Encerra um processo passando o nome do processo ao invés do PID

```bash
killall serviço
```

### Lista a árvore de processos. Mostra um diagrama no qual é possível identificar quem originou (processo pai) cada um dos processos (processo filho).

```bash
pstree
```

### Exibe quais processos estão sendo executados em background e quais processos estão parados no terminal (`jobs`).&#x20;

Executa um processo no terminal (`fg`). Faz com que o terminal fique livre para o uso, inutilizando temporariamente o programa executado (`ctrl + z`). Faz com que o programa execute em background (`bg`)

```bash
jobs
fg
ctrl + z 
bg
```

### Efetua uma busca no sistema operacional para localizar o path dos arquivos

```bash
locate
```

### Atualiza a base de dados que o (`locate`) utiliza para realizar as pesquisas

```bash
updatedb
```

### Exibe o caminho onde se encontra o arquivo de um comando

```bash
which comando
```

### Utilizado para contar o número de palavras, caracteres e linhas que um arquivo possui

```bash
wc -w
wc -c
wc -l
```

### Lista quais pacotes estão disponíveis para instalação a partir de um termo de busca

```bash
apt-cache search mysql-server
```

A opção show do comando apt-cache, mostra informações sobre um determinado pacote

```bash
apt-cache show mysql-server-5.6
```

### Remover pacotes debian

```bash
dpkg -r pacote
```

### Para baixar as dependências

```bash
sudo apt-get -f install
```

### Verifica se está faltando algo para que o pacote possa funcionar corretamente

```bash
./configure
```

### Realizar o build do pacote baixado

```bash
make
```

### Para instalar o pacote

```bash
make install
```

### Copia arquivos para a pasta do servidor remoto

```
scp -r nome-arquivo usuario@ip_servidor:/diretorio
```

### Configurar hora no servidor

```bash
timedatectl set-time '2019-03-16 09:20:00'
```
