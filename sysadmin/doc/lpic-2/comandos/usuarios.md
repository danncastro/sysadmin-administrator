---
description: Usuários
---

# Usuários

### Criando usuário e atribuindo uma senha na criação

```bash
useradd usuario -c "Comentario" -s /bin/bash -m -p $(openssl passwd -crypt senha)
passwd usuario -e
```
