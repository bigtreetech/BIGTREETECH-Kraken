# Klipper
## menuconfig
    [*] Enable extra low-level configuration options
        Micro-controller Architecture (STMicroelectronics STM32) --->
        Processor model (STM32H723) --->
        Bootloader offset (128KiB bootloader (SKR SE BX v2.0)) --->
        Clock Reference (25 MHz crystal) --->
    USB Interface
        Communication interface (USB (on PA11/PA12)) --->
    CANBUS Interface
        Communication interface (CAN bus (on PD0/PD1)) --->
## printer.cfg
See [generic-bigtreetech-kraken.cfg](./generic-bigtreetech-kraken.cfg)

# Marlin
* We can download the source code from [here](https://github.com/bigtreetech/Marlin/tree/Kraken) before Marlin upstream supports this motherboard.


# Writing bootloader for Kraken V1.0
1. Download the [bootloader.bin](./Kraken_H723_bootloader.bin) file to BTT Pi/ Raspberry Pi.
2. Press and hold the boot button of Kraken and then click the reset button to make Kraken goto DFU mode.
3. Run the following command on the Terminal of BTT Pi/ Raspberry Pi to write the bootloader
    ```
    sudo dfu-util -d ,0483:df11 -R -a 0 -s 0x8000000:leave -D ./Kraken_H723_bootloader.bin
    ```
    `0483:df11` is the DFU ID of Kraken (We can get it by running `lsusb` command)</br>
    `./Kraken_H723_bootloader.bin` is the Path of bootloader file.
