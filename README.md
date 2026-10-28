# cachyos-kernel-no-rust

CachyOS default kernel config (linux-cachyos) with Rust support disabled.

Source: https://github.com/CachyOS/linux-cachyos/blob/master/linux-cachyos/config

Changes:

- CONFIG_RUST is not set
- CONFIG_RUST_FW_LOADER_ABSTRACTIONS is not set
- CONFIG_RUST_SERIAL_DEV_BUS_ABSTRACTIONS is not set
- CONFIG_RUST_OVERFLOW_CHECKS is not set
