# stm32f103c8t6-template

Bare-metal C/ASM template for STM32F103C8T6 (Cortex-M3) — custom vector table, linker script and Makefile. No HAL, no CMSIS.

## Contents

- `vector_table.S` — interrupt/exception vectors, weak aliases to a default handler
- `core.S` — `reset_handler`: stack init, copy `.data`, zero `.bss`, jump to `main`
- `STM32F103C8T6.ld` — linker script (memory layout, `_estack`, `_sdata`, `_ebss`, etc.)
- `main.c` — entry point
- `Makefile` — builds with `arm-none-eabi-gcc`

## Build

```bash
make all
```


## Adding an interrupt handler

Define a function with the matching name (e.g. `TIM2_IRQ_handler`) anywhere in your C code — the linker overrides the weak default automatically. Enable it in NVIC and the peripheral's clock/config yourself.

## License

MIT
