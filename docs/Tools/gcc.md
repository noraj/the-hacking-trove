---
tags: [compilation,exploit]
---
# gcc - Cross compilation

From 64bits for 32bits: `gcc -m32`

From 32bits for 64bits: `gcc -m64`

## ArchLinux

### Pre-requisites

To enable 32 bits libraries on ArchLinux, in `/etc/pacman.conf` uncomment:

```ini
[multilib]
Include = /etc/pacman.d/mirrorlist
```

Install multilib gcc:

```
sudo pacman -Syu gcc-multilib gcc-libs-multilib lib32-glibc lib32-libtool lib32-gcc-libs
```

### chroot

[Building in a 32-bit clean chroot - ArchWiki](https://wiki.archlinux.org/index.php/Building_in_a_32-bit_clean_chroot)

### Finding missing lib32 libs

```
$ pkgfile libgcc_s.so.1
core/gcc-libs
core/lib32-gcc-libs
community/aarch64-linux-gnu-gcc
community/riscv64-linux-gnu-gcc

$ pkgfile stubs-32.h   
core/lib32-glibc
community/zig
```

## Troubleshooting

### What is "error while loading shared libraries: requires glibc 2.5 or later dynamic linker"?

[c - gcc: Reduce libc required version - Stack Overflow](https://stackoverflow.com/questions/12075403/gcc-reduce-libc-required-version)

`gcc -m32 -Wl,--hash-style=both`

### old version of glibc

```
/tmp/15285_32: /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by /tmp/15285_32)
/tmp/15285_32: /lib/tls/libc.so.6: version `GLIBC_2.7' not found (required by /tmp/15285_32)
```

So use an old glibc in LDPRELOAD or compile with `-static`, ex: `gcc -m32 -Wl,--hash-style=both -static -o 15285_32 15285.c`

## Find target version of glibc

```
$ ldd --version
ldd (GNU libc) 2.3.4
```

## Find old glibc tarballs:

[Index of /gnu/glibc](https://ftp.gnu.org/gnu/glibc/)

## OLD machines

- CentOS: 
    - Dwonload [Download - CentOS Wiki](https://wiki.centos.org/Download)
    - Fix repo [CentOS 5 Repository fix using vault.centos.org \| Bots!](https://tweenpath.net/centos-5-repository-fix-using-vault-centos-org/)
