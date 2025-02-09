To build:
For loading a BOLOS application to a Ledger device, Ledger has actually written a command, called [Cargo Ledger](https://github.com/LedgerHQ/cargo-ledger). This we need to install with:
```
cargo install --git https://github.com/LedgerHQ/cargo-ledger
```

Next up we need install the supporting Python libraries from Ledger to control Ledger devices, [LedgerCTL](https://github.com/LedgerHQ/ledgerctl). This we do with:
```
pip3 install --upgrade protobuf setuptools ecdsa
pip3 install ledgerwallet
```

Lastly install the ARM GCC toolchain: `arm-none-eabi-gcc` for your OS. We are using MacOS, so we can use brew with:
```
brew install armmbed/formulae/arm-none-eabi-gcc
```

to build:
cargo +nightly ledger build {TARGET} -- -Zbuild-std=std,alloc
with TARGET = nanosplus, nanos, etc.
to load: cargo +nightly ledger build nanosplus --load -- -Zbuild-std=std,alloc

