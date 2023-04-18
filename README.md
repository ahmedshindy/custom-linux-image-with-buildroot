### Set Up

1. Get buildroot & build for qemu emulator

There is default config files available for many targets including qemu
```shell
wget https://buildroot.org/downloads/buildroot-2023.02.tar.gz
cd buildroot-2023.02/
make qemu_arm_versatile_defconfig
make
```

2. You should have qemu emulator installed on your system
for me I built it from source code following these instructions

```shell
	wget https://download.qemu.org/qemu-8.0.0-rc2.tar.xz
	tar xvJf qemu-8.0.0-rc2.tar.xz
	cd qemu-8.0.0-rc2
	./configure
	make
```
### OR 
I think you can work with the one available on ubuntu packages, it is not the 
latest version but for this example it should work fine isa.
to search for the available package 
```shell
apt-cache search qemu-system-arm
```
to install run,
`sudo apt-get update`
`sudo apt-get install qemu-system-arm`
check your installation 
`qemu-system-arm --help`
you should get lots of info printed, don't read them haha..^--^

2. Run
```shell
qemu-system-arm -M versatilepb -m 256 \
-kernel output/images/zImage \
-dtb output/images/versatile-pb.dtb \
-drive file=output/images/rootfs.ext2,if=scsi,format=raw \
-append "root=/dev/sda console=ttyAMA0,115200" \
-serial stdio -net nic,model=rtl8139 -net user
```
log in as root, with no password.
![shot1](./buildroot-quickstart/Screenshot%20from%202023-04-17%2014-53-30.png)

[Watch video](./buildroot-quickstart/buildroot-quickstart.mkv)
