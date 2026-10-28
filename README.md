# cachyos-kernel-no-rust

CachyOS default kernel config (linux-cachyos) with Rust support disabled.

Source: https://github.com/CachyOS/linux-cachyos/blob/master/linux-cachyos/config

Changes:

- CONFIG_RUST is not set
- CONFIG_RUST_FW_LOADER_ABSTRACTIONS is not set
- CONFIG_RUST_SERIAL_DEV_BUS_ABSTRACTIONS is not set
- CONFIG_RUST_OVERFLOW_CHECKS is not set

## Usage

Drop-in replacement for the default linux-cachyos config. No Rust toolchain
(rustc, bindgen) is needed to build.

### With the CachyOS PKGBUILD

1. Clone the packaging repo:

   ```
   git clone https://github.com/CachyOS/linux-cachyos.git
   cd linux-cachyos/linux-cachyos
   ```

2. Replace the shipped config with this one:

   ```
   curl -L -o config https://raw.githubusercontent.com/based-software/cachyos-kernel-no-rust/master/config
   ```

3. Build and install:

   ```
   makepkg -si
   ```

### Standalone against a vanilla kernel tree

1. Get the matching kernel source (config targets 7.3.x):

   ```
   git clone --depth 1 --branch v7.3 https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git
   cd linux
   ```

2. Copy the config in place and resolve it against your source:

   ```
   curl -L -o .config https://raw.githubusercontent.com/based-software/cachyos-kernel-no-rust/master/config
   make olddefconfig
   ```

3. Build and install:

   ```
   make -j"$(nproc)"
   sudo make modules_install install
   ```

`make olddefconfig` silently drops the stale RUSTC_* toolchain-detection
lines, so no Rust toolchain is required at any step.
