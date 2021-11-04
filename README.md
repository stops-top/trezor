# Trezor 


```sh
sudo apt-get install scons gcc-arm-none-eabi libnewlib-arm-none-eabi llvm-dev libclang-dev clang
pip3 install trezor

```

Install the appropriate target with [`rustup`](https://rustup.rs/):

```sh
rustup target add thumbv7em-none-eabihf  # for TT
rustup target add thumbv7m-none-eabi     # for T1
rustup update
```

use Poetry to install and track Python dependencies.

```sh
git submodule update --init --recursive --force
sudo pip3 install poetry
poetry install
poetry shell
```


```sh
make vendor build_boardloader build_bootloader build_firmware
```


## Documentation

See the `docs` folder or visit [docs.trezor.io](https://docs.trezor.io).
