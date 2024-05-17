---
description: Volumes / Discos
---

# Volumes / Discos

### Dentries e inodes

Para limpar  Dentries e inodes

```bash
sudo -i
sync; echo 1 > /proc/sys/vm/drop_caches
```

***

### Cache/Buffer

Para limpar tudo: Cache/Buffer, Dentries e Inodes

```bash
sudo -i
sync; echo 2 > /proc/sys/vm/drop_caches
```

***

### LVM

```bash
vgs
```

```bash
fdisk -l
```

```bash
pvcreate /dev/sdb
```

```bash
vgextend system /dev/sdb
```

```bash
cat /etc/fstab
```

```basic
lvextend -L +5GB /dev/mapper/system-var && xfs_growfs /dev/mapper/system-var
```

```bash
df -h
```

```bash
lsblk -l
```

```bash
vgdisplay
```

```bash
pvdisplay
```

```bash
lvdisplay
```

```bash
lvextend -l +30%FREE /dev/vg_sys/lv_root
lvextend -L +1GB /dev/mapper/system-var
```

```bash
resize2fs  /dev/vg_sys/lv_root
xfs_growfs /dev/mapper/system-var
```

***

### Particionamento

Particionando e formatando discos via terminal

```bash
fdisk /dev/disco
```

```bash
Command: n
Select: p
Partition number: 1
First sector: enter
Last sector: enter
Command: w
```

```bash
mkfs.ext4 /dev/disco
```

***

### Mounts / Umounts

Montando e desmontando discos

```bash
mkdir diretorio_aonde_sera_montado_o_disco
mount /dev/disco /diretorio_aonde_sera_montado_o_disco
```

```bash
umount /dev/disco
```

Montando discos automaticamente

```bash
lsblk
vi /etc/fstab
```

```bash
/dev/disco /diretorio_aonde_sera_montado_o_disc ext4 defaults 0 0
```

***
