# Project Setup

## Create new project

* Create new project `cargo new project_name`
* Create `.cargo/config.toml` on project folder
* Create `Embed.toml` in project folder
* Create `memory.x` in project folder

See `example_files` folder for samples.

## Find the right chip

This command will list out all the chips cargo knows about.

```console
> cargo embed --list-chips
```

## Configuration Examples

### STM32F303

#### config.toml

```toml
[target.thumbv7em-none-eabi]

# use the Tlink.x scrip from the cortex-m-rt crate
rustflags = [
  "-C", "link-arg=-Tlink.x",
]

[build]
target = "thumbv7em-none-eabi"
```

#### Cargo.toml

[F3xx HAL](https://github.com/stm32-rs/stm32f3xx-hal)

```toml
[dependencies.stm32f3xx-hal]
version = "0.9.1"
features = ["stm32f303xe", "rt"]
```

#### memory.x

```c
/* memory.x - Linker script for the STM32F303ZET6 */
MEMORY
{
  /* Flash memory begins at 0x80000000 and has a size of 512KB*/
  FLASH : ORIGIN = 0x08000000, LENGTH = 512K
  /* RAM begins at 0x20000000 and has a size of 64kB*/
  RAM : ORIGIN = 0x20000000, LENGTH = 64K
}
```

#### Compile

```console
> cargo build --target thumbv7em-none-eabi --release
```

#### Flash

```console
> cargo flash --target thumbv7em-none-eabi --chip STM32F303ZETx --release
```

### STM32F746

#### config.toml

```toml
[target.thumbv7em-none-eabi]

# use the Tlink.x scrip from the cortex-m-rt crate
rustflags = [
  "-C", "link-arg=-Tlink.x",
]

[build]
target = "thumbv7em-none-eabi"
```

#### Cargo.toml

[F7xx HAL](https://github.com/stm32-rs/stm32f7xx-hal)

```toml
[dependencies.stm32f7xx-hal]
version = "0.7.0"
features = ["stm32f746", "rt"]
```

#### memory.x

```c
/* memory.x - Linker script for the STM32F746zgt6 */
MEMORY
{
  /* Flash memory begins at 0x80000000 and has a size of 1MB*/
  FLASH : ORIGIN = 0x08000000, LENGTH = 1M
  /* RAM begins at 0x20000000 and has a size of 320kB*/
  RAM : ORIGIN = 0x20000000, LENGTH = 320K
}
```

#### Compile

```console
> cargo build --target thumbv7em-none-eabi --release
```

#### Flash

```console
> cargo flash --target thumbv7em-none-eabi --chip STM32F746ZGTx --release
```