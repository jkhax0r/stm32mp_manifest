# oe-manifest
This project is the repo manifest of OpenSTLinux release.
# STM32MPU-Ecosystem-v6.1.0 release TAG: openstlinux-6.6-yocto-scarthgap-mpu-v25.06.11

See the wiki user guide for more information: https://wiki.st.com/stm32mpu/wiki/STM32MPU_Distribution_Package

# Getting Started
To build and image, initialize and sync the repositores using the repo tool

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
