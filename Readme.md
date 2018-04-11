fclkcfg kernel module debian package
====================================================================================

Overview
------------------------------------------------------------------------------------

### Introduction

This is a repository for making fclkcfg kernel module debian package.

Fclkcfg is a FPGA Clock Configuration Device Driver.

For details of fclkcfg, please refer to following URL.

  * https://github.com/ikwzm/fclkcfg

Build Debian Package
------------------------------------------------------------------------------------

### Download repository

```console
shell$ git clone --recursive --depth=1 -b v1.0.0 git://github.com/ikwzm/fclkcfg-kmod-dpkg
shell$ cd fclkcfg-kmod-dpkg
```

### Cross Compile

#### Parameters

| Parameter Name | Description              | Default Value                                                    |
|----------------|--------------------------|------------------------------------------------------------------|
| kernel_release | Kernel Release Name      | $(shell uname -r)                                                |
| arch           | Architecture Name        | $(shell uname -m \| sed -e s/arm.\*/arm/ -e s/aarch64.\*/arm64/) |
| deb_arch       | Debian Architecture Name | $(shell dpkg --print-architecture)                               |
| kernel_src_dir | Kernel Source Directory  | /lib/modules/$(kernel_release)/build                             |


```console
shell$ sudo debian/rules arch=arm deb_arch=armhf kernel_release=4.14.21-armv7-fpga kernel_src_dir=/usr/src/linux-4.14.21-armv7-fpga binary
    :
    :
    :
shell$ file ../fclkcfg-4.14.21-armv7-fpga_1.0.0-1_armhf.deb
../fclkcfg-4.14.21-armv7-fpga_1.0.0-1_armhf.deb: Debian binary package (format 2.0)
```

### Self Compile

```console
shell$ sudo debian/rules binary
    :
    :
    :
shell$ file ../fclkcfg-4.14.21-armv7-fpga_1.0.0-1_armhf.deb
../fclkcfg-4.14.21-armv7-fpga_1.0.0-1_armhf.deb: Debian binary package (format 2.0)
```

