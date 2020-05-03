# Console
Source taken from variscite Thud var01
   git clone https://github.com/varigit/meta-variscite-boot2qt.git -b thud-var01

   our changes will be on top of it.
   
  **Build_environment original**
  *cd meta-console-var-bt2q*
  *./b2qt-init-build-env mirror* 
  *.mkdir ~/var-b2qt-mirror*
  *mv *.git ~/var-b2qt-mirror*
  *./b2qt-init-build-env init --reference ~/var-b2qt-mirror --device imx6ul-var-dart*

  **Set up environment**
  *MACHINE=imx6ul-var-dart source ./setup-environment.sh*

  **Compile Yocto**
  *MACHINE=imx6ul-var-dart bitbake b2qt-embedded-qt5-image*

  **Create a toolchain**
  *MACHINE=imx6ul-var-dart bitbake meta-toolchain-b2qt-embedded-qt5-sdk*

  **target rootfs image**
  *~/var-b2qt/meta-variscite-boot2qt/build-imx6ul-var-dart/tmp/deploy/images/imx6ul-var-dart/b2qt-embedded-qt5-image-imx6ul-var-dart.img*

  **toolchain installation script**
  *~/var-b2qt/meta-variscite-boot2qt/build-imx6ul-var-dart/tmp/deploy/sdk/b2qt-x86_64-meta-toolchain-b2qt-embedded-qt5-sdk-imx6ul-var-dart.sh*

  **Flash to SD-CARD**

  *sudo umount /dev/sdX*
  *sudo dd if=tmp/deploy/images/imx6ul-var-dart/b2qt-embedded-qt5-image-imx6ul-var-dart.wic of=/dev/sdX bs=1M && sync*

  **Create Extended SD-CARD   -  a scrip to flash & burn version to NAND**

  $ cd ~/var-b2qt/meta-variscite-boot2qt
  $ $ sudo MACHINE=imx6ul-var-dart sources/meta-variscite-fslc/scripts/var_mk_yocto_sdcard/var-create-yocto-sdcard.sh /dev/sdX
