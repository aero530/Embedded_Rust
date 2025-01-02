# Dev Env Setup for Windows

## Rust Setup

Follow instructions at [https://rustup.rs/](https://rustup.rs/)

### Intall Rust Arm targets

```console
> rustup target add thumbv6m-none-eabi
> rustup target add thumbv7m-none-eabi
> rustup target add thumbv7em-none-eabi
> rustup target add thumbv7em-none-eabihf
```

### Install [Cargo Flash](https://github.com/probe-rs/probe-rs/tree/master/cargo-flash) & [Cargo Embed](https://github.com/probe-rs/probe-rs/tree/master/cargo-embed)

```console
> cargo binstall probe-rs-tools
```

## Install arm-none-eabi-gdb

ARM provides `.exe` installers for Windows. Grab one from [here](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads), and follow the instructions. Just before the installation process finishes tick/select the "Add path to environment variable" option. Then verify that the tools are in your `%PATH%`:

Verify gcc is installed:

``` console
> arm-none-eabi-gcc -v
```

The results should be something like:

```console
(..)
$ arm-none-eabi-gcc -v
gcc version 5.4.1 20160919 (release) (..)
```

## OpenOCD

There's no official binary release of OpenOCD for Windows but there are unofficial releases
available [here](https://github.com/xpack-dev-tools/openocd-xpack/releases). Grab the 0.10.x zipfile and extract it somewhere in your drive (I recommend `C:\OpenOCD` but with the drive letter that makes sense to you) then update your `%PATH%` environment variable to include the following path: `C:\OpenOCD\bin` (or the path that you used before).

Verify OpenOCD is installed and in your `%PATH%` with:

``` console
> openocd -v
```

The results should be something like:

``` console
$ openocd -v
Open On-Chip Debugger 0.10.0
(..)
```

## ST-LINK USB driver

You'll also need to install [this USB driver] or OpenOCD won't work. Follow the installer instructions and make sure you install the right (32-bit or 64-bit) version of the driver.

[this USB driver]: http://www.st.com/en/embedded-software/stsw-link009.html
