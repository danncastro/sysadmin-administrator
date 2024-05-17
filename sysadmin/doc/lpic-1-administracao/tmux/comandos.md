---
description: Comandos
---

# Comandos

#### Informações

**O asterisco informa em qual janela estou no momento**

```bash
tmux # Cria uma nova sessão que sera fechada ao sair
```

```bash
tmux new -s nome_sessão # Cria uma nova sessão mantendo-a ativa mesmo que seia da sessão
```

```bash
tmux ls # Lista as sessões que estão ativas no momento
```

```bash
tmux attach -t nome_sessão # Entra novamente na sessão que está em execução
```

```bash
tmuxinator new nome-sessão # Cria uma sessão que pode ser gerenciada
nome: nome-sessão
root: /caminho/do/projeto

windows:
    - VIM: vim .
    - DANGER ZONE:
        layout: main-horizontal
        panes:
            - git fetch --all
            - git status
```

```bash
tmuxinator nome-sessão # Abre a sessão criada pelo gerenciador
```
