# u-root builder

This repository holds no code and just builds [u-root](https://u-root.org)
images via GitHub Actions.

## Try it out

Download a prebuilt u-root image from
[releases](https://github.com/linuxboot/u-root-builder/releases):

```sh
curl -L -o u-root.cpio.xz https://github.com/linuxboot/u-root-builder/releases/download/v0.0.1/u-root_amd64_all.cpio.xz
```

Download a
[kernel from Arch Linux](https://archlinux.org/packages/core/x86_64/linux/)
and extract it:

```sh
curl -L -o linux.tar.zst https://archlinux.org/packages/core/x86_64/linux/download/
tar -xf linux.tar.zst
```

Run it:

```sh
qemu-system-x86_64 -enable-kvm -machine q35 -nographic -append "console=ttyS0" \
  -kernel usr/lib/modules/*/vmlinuz -initrd u-root.cpio.xz
```

Run a command:

```sh
uname -a
```

![asciinema recording of u-root](u-root.gif)
