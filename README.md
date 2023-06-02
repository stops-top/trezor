# [Firmware](https://docs.trezor.io)

辅助模块+安全单元，模范工程



```sh
sudo apt-get install scons llvm-dev libclang-dev clang protobuf-compiler
sudo pip3 install trezor
sudo pip3 install poetry

```



在官网下载指定版本安装 [`arm-gnu-toolchain`](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads)

```sh
wget https://developer.arm.com/-/media/Files/downloads/gnu/12.2.mpacbti-rel1/binrel/arm-gnu-toolchain-12.2.mpacbti-rel1-x86_64-arm-none-eabi.tar.xz
sudo mkdir -p /opt/gcc-arm/
sudo tar xvf arm-gnu-toolchain-12.2.mpacbti-rel1-x86_64-arm-none-eabi.tar.xz -C /opt/gcc-arm/
```

在~/.bashrc中添加 

```
PATH=$PATH:/opt/gcc-arm/arm-gnu-toolchain-12.2.mpacbti-rel1-x86_64-arm-none-eabi/bin
```
网络环境比较差的情况下，不推荐 PPA 安装
```sh
sudo add-apt-repository ppa:team-gcc-arm-embedded/ppa
sudo apt-get update

sudo apt-get install gcc-arm-embedded
sudo apt-get remove gnu-arm-embedded
sudo apt-get remove gcc-arm-none-eabi
sudo apt-get install gcc-arm-none-eabi

```

---

Install the appropriate target with [`rustup`](https://rustup.rs/):

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

rustup target add thumbv7em-none-eabihf  # for TT
rustup target add thumbv7m-none-eabi     # for T1
rustup update
```

use Poetry to install and track Python dependencies.

`poetry`是一个Python虚拟环境和依赖管理的工具，poetry和pipenv类似，另外还提供了打包和发布的功能。

```sh
git submodule update --init --recursive --force
poetry install
poetry shell
```

编译对应的三层固件
```sh
make vendor build_boardloader build_bootloader build_firmware
```

编译模拟固件
```sh
git submodule update --init --recursive --force
poetry install
poetry shell

poetry install --sync
```


```sh
cd core
make vendor build_unix
```


