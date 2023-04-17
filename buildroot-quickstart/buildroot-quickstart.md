1. Install & build for qemu emulator
```shell
wget https://buildroot.org/downloads/buildroot-2023.02.tar.gz
cd buildroot-2023.02/
make qemu_arm_versatile_defconfig
make
```
2. Run and log in as root, with no password
```shell
qemu-system-arm -M versatilepb -m 256 \
-kernel output/images/zImage \
-dtb output/images/versatile-pb.dtb \
-drive file=output/images/rootfs.ext2,if=scsi,format=raw \
-append "root=/dev/sda console=ttyAMA0,115200" \
-serial stdio -net nic,model=rtl8139 -net user
```
![shot1](./Screenshot%20from%202023-04-17%2014-53-30.png)

[Watch video](./buildroot-quickstart.mkv)
