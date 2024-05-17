---
description: Reset Password Root
---

# Reset Password Root

### Etapa 1:&#x20;

acessar o menu de inicialização Reinicie o sistema e toque na tecla Esc cerca de uma vez por segundo para iniciar o menu GRUB.

### Etapa 2:

Editar opções de inicialização Use as setas para realçar a versão do Linux na qual inicializou e pressione `e`

Use as setas para destacar a linha que começa com kernel ou Linux.

Pressione E. \_

No final da linha, adicione um espaço e digite single . Pressione Enter e inicialize no modo de usuário único pressionando Ctrl-X ou B . (O sistema exibirá o comando a ser usado.)

### Etapa 3:&#x20;

Remontar a unidade Você deve ter uma linha de comando e terá privilégios de root. Para ativar o acesso de leitura/gravação em seu disco rígido, digite o seguinte:&#x20;

```bash
mount / -o remount,rw
```

### Etapa 4:&#x20;

Alterando a Senha Digite o seguinte: `passwd` Pressione Enter e o sistema deve solicitar que você insira e confirme uma nova senha.

### Passo 5:&#x20;

Reiniciar Digite o seguinte, pressionando enter após cada linha:&#x20;

```bash
mount / -o remount,ro sync reboot
```
