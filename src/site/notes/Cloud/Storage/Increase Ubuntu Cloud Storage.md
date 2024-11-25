---
{"dg-publish":true,"permalink":"/cloud/storage/increase-ubuntu-cloud-storage/"}
---



- [Ubuntu: Extend your default LVM space - Packet Pushers](https://packetpushers.net/ubuntu-extend-your-default-lvm-space/)
- https://netshop-isp.com.cy/blog/how-to-extend-lvm-disk-on-linux-ubuntu-20-04/
- https://www.tecmint.com/extend-and-reduce-lvms-in-linux/
- https://networklessons.com/uncategorized/extend-lvm-partition
- https://askubuntu.com/questions/1406697/extend-lvm-size

For [[CentOS\|CentOS]] see [[Increase CentOS Cloud Storage\|Increase CentOS Cloud Storage]]

## Important Commands

- [[lsblk\|lsblk]]
- [[pvresize\|pvresize]]
- [[cfdisk\|cfdisk]]


## Get logical volume path

```bash
lvdisplay | less
```


### Example 

```
/dev/ndc-vg/lv-opt
```

```
/dev/ndc-vg/lv-var
```

```
/dev/centos76_vg/root
```

```
/dev/rhel_pkica01/opt
```

```
/dev/ubuntu-vg/ubuntu-lv
```

```
/dev/vg_ndc/root
```

```
/dev/ubuntu-vg/lv-root
```
## Extend logical volume

```bash
cfdisk
```

alternative [[parted\|parted]]

### Extend Physical Volume

```bash
pvresize /dev/vda3
```

```
pvresize /dev/sda3
```
## Check if extended

```
pvs
```
### Extend Logical Volume

```
lvextend -l +80G /dev/ndc-vg/lv-opt
```

```
lvextend -l +100%FREE /dev/ndc-vg/lv-var
```

```
lvextend -l +100%FREE /dev/centos76_vg/root
```

```
lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
```

```
lvextend -l +100%FREE /dev/ubuntu-vg/lv-root
```

### Resize blocks

From [[df\|df]]

```bash
resize2fs /dev/mapper/ndc--vg-lv--opt
```

```
resize2fs /dev/mapper/ndc--vg-lv--var
```

```bash
resize2fs /dev/mapper/centos76_vg-root
```

```
resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

```
resize2fs /dev/mapper/ubuntu--vg-lv--root
```