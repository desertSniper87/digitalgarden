---
{"dg-publish":true,"permalink":"/increase-cent-os-cloud-storage/"}
---



## Data Disk

https://serverfault.com/questions/861517/centos-7-extend-partition-with-unallocated-space

### Create Physical Volume

```bash
sudo pvcreate /dev/vdd
```


### Extend volume group 

```bash
sudo vgextend centos76_vg /dev/vdd
```

## Extend Logical Volume

```bash
lvextend -l +100%FREE /dev/centos76_vg/root
```

### Resize filesystem

```bash
sudo resize2fs /dev/mapper/centos76_vg-root
```