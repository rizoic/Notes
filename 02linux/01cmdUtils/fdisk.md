# FDISK

## Get drive path for mounting
For ubuntu 16.04: At times you may plug and external hard disk and it will be absent from the listing post `df -h`. In this case you can run this series of commands and then mount this hard disk

```bash
# This will give you a list of all the partitions. Use this to get a path to your mounted disk. See towards the bottom it would be something like e.g. /dev/sdb1 
sudo fdisk -l
# You you have this path you can mount it using the followin command
sudo mount /dev/sdb1 /mnt/
# Now this hard disk will be accessible at /mnt/
```