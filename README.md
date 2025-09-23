# Turing RK1 Bootloader
This is a brief summary of how to create a recent bootloader for the Turing RK1 board. The following instructions are based on the work of [@Quozul](https://github.com/Quozul), who summarized the steps on this page: [Build Custom Image for Turing Pi RK1](https://quozul.dev/posts/2024-10-12-build-custom-image-for-turing-pi-rk1/).

## Obtain required code and artifacts
First, clone the U-Boot repository and download the necessary files:
```
git clone https://source.denx.de/u-boot/u-boot.git
mkdir u-boot/rkbin
curl -LJO --output-dir u-boot/rkbin https://github.com/rockchip-linux/rkbin/raw/refs/heads/master/bin/rk35/rk3588_bl31_v1.51.elf
curl -LJO --output-dir u-boot/rkbin https://github.com/rockchip-linux/rkbin/raw/refs/heads/master/bin/rk35/rk3588_ddr_lp4_2112MHz_lp5_2400MHz_v1.19.bin
```

## Start the container and mount the source directory
Use the following command to start a Docker container and mount the source directory:
```
docker run -it -v ./u-boot:/mnt gcc:15.2.0 /bin/bash
```

### Prepare the compilation environment inside the container
Once in the container, navigate to the mounted directory and set up the build configuration:
```
apt-get update && apt-get install -y bison make flex python3-pyelftools python3-setuptools swig

cd /mnt

make turing-rk1-rk3588_defconfig

ROCKCHIP_TPL=rkbin/rk3588_ddr_lp4_2112MHz_lp5_2400MHz_v1.19.bin \
BL31=rkbin/rk3588_bl31_v1.51.elf \
make -j

dd if=/dev/zero of=bootloader.img bs=512 count=32767
dd if=./idbloader.img of=bootloader.img bs=512 seek=64 conv=notrunc
dd if=./u-boot.itb of=bootloader.img bs=512 seek=16384
```

# Obtain the boot image
The generated boot image will be located at the root of the cloned U-Boot repository and will be named `bootloader.img`. This image can be deployed using the Turing Pi 2 BMC Web UI or the TPI CLI.
