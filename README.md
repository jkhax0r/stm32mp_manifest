# oe-manifest
This project is the repo manifest of OpenSTLinux release.
# STM32MPU-Ecosystem-v6.1.0 release TAG: openstlinux-6.6-yocto-scarthgap-mpu-v25.06.11

See the wiki user guide for more information: https://wiki.st.com/stm32mpu/wiki/STM32MPU_Distribution_Package

# OV585 repos

OV585 distro layer: https://github.com/jkhax0r/meta-st-ov585

OV585 STM32MP addons layer: https://github.com/jkhax0r/meta-ov585-stm32mp-addons

# Getting Started
To build and image, initialize and sync the repositores using the repo tool

This setup is tested and used on Ubuntu 24.04, and should also work on Ubuntu 22.04.

```repo init -u https://github.com/jkhax0r/stm32mp_manifest.git -b scarthgap -m ov585.xml```

```repo sync```

Initialize the environment and chose the MACHINE and DISTRO using the scripts provided.

``` source ./layers/meta-st/meta-st-ov585/scripts/envsetup.sh```

You should end up with output similar to this:

```
===========================================================================
Configuration files have been created for the following configuration:

    DISTRO            :  ov585-openstlinux-weston
    DISTRO_CODENAME   :  scarthgap
    MACHINE           :  stm32mp25-cargt-ov585
    BB_NUMBER_THREADS :  <no-custom-config-set>
    PARALLEL_MAKE     :  <no-custom-config-set>

    BUILDDIR          :  build-ov585openstlinuxweston-stm32mp25-cargt-ov585
    DOWNLOAD_DIR      :  <disable>
    SSTATE_DIR        :  <disable>

    SOURCE_MIRROR_URL :  <no-custom-config-set>
    SSTATE_MIRRORS    :  <disable>

    WITH_EULA_ACCEPTED:  <no-custom-config-set>

===========================================================================
```

You can now start a build with a command like this:

```bitbake ov585-cargt-image-dev```

# Program the CARGT dev board

Set the boot mode to Serial Downloader for programming. After programming, set it back to eMMC boot.

| BOOT_MODE[1:0] | Boot Configuration | Notes |
| --- | --- | --- |
| 00 | Boot from Internal Fuses | |
| 01 | Serial Downloader | Production programming |
| 10 | USDHC1 8-bit eMMC 5.1 | Recommended setting |
| 11 | USDCH2 4-bit SD | Default setting |

Only `01` and `10` are normally relevant for OV585 programming and eMMC boot.

For DFU/programming, use the USB port closest to the Ethernet jack.

Flash the eMMC image from WSL/Linux using the Windows STM32CubeProgrammer CLI:

```./layers/meta-st/meta-st-ov585/scripts/flash-ov585.sh```

The script expects the Windows programmer binary at:

```/mnt/c/Program Files/STMicroelectronics/STM32Cube/STM32CubeProgrammer/bin/STM32_Programmer_CLI.exe```
