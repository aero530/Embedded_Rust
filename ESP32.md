# ESP32

## Generate new project from template
```bash
cargo generate esp-rs/esp-idf-template cargo
```

Windows projects must add `ESP_IDF_PATH_ISSUES = 'warn'` to the `[env]` section of `.cargo/config.toml`.

## Compile project

```bash
cargo build
```

## Flash code

```bash
espflash flash target/<mcu-target>/debug/<project-name>
```
## Monitor

```bash
espflash monitor /dev/ttyUSB0
```

## Links

* [ESP32 C6 Dev Kit N8](https://www.waveshare.com/esp32-c6-dev-kit-n8.htm)
* [ESP32 C6 Dev Kit Ref](https://docs.espressif.com/projects/espressif-esp-dev-kits/en/latest/esp32c6/esp32-c6-devkitc-1/user_guide.html#hardware-reference)
* [ESP32 C6 HAL](https://github.com/esp-rs/esp-hal/tree/main/esp32c6-hal)
* [ESP32 C6 HAL Docs](https://docs.rs/esp32c6-hal/latest/esp32c6_hal/)
* [The Rust on ESP Book](https://esp-rs.github.io/book/overview/using-the-standard-library.html)


## Linux Setup

### Setup Rust
```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential pkg-config libssl-dev libudev-dev
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
**restart terminal**

### Setup ESP Requirements & Tooling
```bash
sudo apt-get install git wget flex bison gperf python3 python3-pip python3-venv cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0
cargo install espup
espup install
cargo install cargo-generate
cargo install ldproxy
cargo install cargo-espflash
cargo install espflash
```

### Setup env variables

* Add the environment variables to your shell profile directly:

* Add the content of $HOME/export-esp.sh to your shell’s profile: `cat $HOME/export-esp.sh >> [path to profile]`, for example, `cat $HOME/export-esp.sh >> ~/.bashrc`.

Refresh the configuration by restarting the terminal session or by running source [path to profile], for example, source ~/.bashrc.

## Windows Setup (Power Shell)

### Install Python

If not already setup, install [Python](https://www.python.org/downloads/windows/).

### Install build tools for ESP
```bash
cargo install espup
espup install
cargo install cargo-generate
cargo install ldproxy
cargo install cargo-espflash
cargo install espflash
```
**Restart vs code**

**I had to manually copy paste the lines from `C:\Users\username\export-esp.ps1` into a power shell terminal to get the env variables to work**

```powershell
$Env:LIBCLANG_PATH = "C:\Users\phil\.rustup\toolchains\esp\xtensa-esp32-elf-clang\esp-clang\bin\libclang.dll"
$Env:PATH = "C:\Users\phil\.rustup\toolchains\esp\xtensa-esp32-elf-clang\esp-clang\bin;" + $Env:PATH
$Env:PATH = "C:\Users\phil\.rustup\toolchains\esp\xtensa-esp-elf\bin;" + $Env:PATH
```

> ----
> Project folder must be at root of drive so the path names are short.  Building the esp toolchain will fail if the path names are too long.
> ----

## WSL Setup

WSL does not support USB interface so you can not program the device.  This setup can only be used to build the binary that would then get programmed from power shell using espflash.

### **Install WSL**

#### Install using Command Prompt

1. Start CMD with administrative privileges.
2. Execute `wsl --install` command.
3. Run `wsl -l -o` to list other Linux releases.
4. You can install your favorite Linux distribution, use `wsl --install -d NameofLinuxDistro.`

When the operation is finished, restart your PC. You can start the Linux distribution from your Start menu.

#### Install Using Windows Features
1. Open the Start menu and type "Windows features" into the search bar and click on "Turn Windows Features On or Off".
2. Tick the "Windows Subsystem for Linux" checkbox and press the “OK” button.
3. When the operation is complete, you will be asked to restart your computer.
4. After that, use the Microsoft Store app and look for the Linux distribution you want to use.
5. Install the Linux distro of your choice.
Step 4:The Linux distribution can be launched from the Start menu.


### Setup Rust
```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential pkg-config libssl-dev
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
**restart terminal**

### Setup ESP Requirements & Tooling
```bash
cargo install espup
espup install
cargo install cargo-generate
cargo install ldproxy
sudo apt-get install git wget flex bison gperf python3 python3-pip python3-venv cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0
```

### Setup env variables

* Add the environment variables to your shell profile directly:

* Add the content of $HOME/export-esp.sh to your shell’s profile: `cat $HOME/export-esp.sh >> [path to profile]`, for example, `cat $HOME/export-esp.sh >> ~/.bashrc`.

Refresh the configuration by restarting the terminal session or by running source [path to profile], for example, source ~/.bashrc.
