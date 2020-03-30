# casper
An experimental virtualization kernel written in C.

# Building
## Cross-compilation with GNU Compiler Collection
In order to build the software you must cross-compile to target `i686-elf`.

## GNU xorriso (POSIX to ISO9660)
You will need to install `xorriso` if you wish to build a ready-to-run ISO.

---

To build the binary alone:
```bash
make
```

To build a bootable disc image which can be used directly on hardware or with virtualization platforms like `qemu` and `vmware`:
```bash
make image
```
