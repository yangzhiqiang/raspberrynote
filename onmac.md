在Mac下制作启动盘

1. 使用磁盘工具或者`diskutil list`命令查看相应的启动盘所在的磁盘名称。类似'diskn'等。
2. 使用`sudo diskutil unmountDisk /dev/diskn`来unmount指定的磁盘，否则会提示‘device busy’
3. 使用`sudo dd bs=1m if=pathof.img of=/dev/diskn`制作相应的启动盘。
