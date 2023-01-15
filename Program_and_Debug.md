# Program & Debug

## Build Code

```bash
> cargo build --target thumbv6m-none-eabi --release
```

* Use thumbv6m-none-eabi for ARM Cortex-M0 and Cortex-M0+
* Use thumbv7m-none-eabi for ARM Cortex-M3
* Use thumbv7em-none-eabi for ARM Cortex-M4 and Cortex-M7 (no FPU support)
* Use thumbv7em-none-eabihf for ARM Cortex-M4F and Cortex-M7F (with FPU support)

## Flash

```bash
> cargo flash --target thumbv6m-none-eabi --chip STM32G031K8Tx --release
```

## Build and Flash

```bash
> cargo embed --target thumbv6m-none-eabi --release
```

## Debug

### [Using Cargo Embed](https://docs.rust-embedded.org/discovery/microbit/05-led-roulette/debug-it.html)

Compile, flash, & start debug server

```bash
> cargo embed --target thumbv6m-none-eabi --chip STM32G031K8Tx
```

In a new terminal start GDB

```bash
> arm-none-eabi-gdb -q -ex "target remote :1337" target/thumbv6m-none-eabi/debug/blink
```

### [Using OpenOCD](https://docs.rust-embedded.org/discovery/f3discovery/05-led-roulette/debug-it.html)

Start OpenOCD

```bash
> openocd -s C:\OpenOCD\share\scripts -f interface/stlink.cfg -f target/stm32l0x.cfg
```

In a new terminal start GDB

```bash
> arm-none-eabi-gdb -q -ex "target remote :3333" target/thumbv6m-none-eabi/debug/blink
```
