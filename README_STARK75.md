# HOWTO BUILD WITH CH347 SUPPORT
## MAYBE YOU HAVE TO ADD EXTRA DEPENDENCIES TAKE A LOOK TO THE OTHER README FILES

> ./configure --enable-ch347
> make
> make install
> sudo openocd -f target/ch347.cfg -c "transport select jtag" -f cpld/xilinx-xc7.cfg -c "init;scan_chain"

# ENABLE USB-SPI BRIDGE
## TO FLASH OR INTERACT WITH DMA CARD INTERNAL SPI MEMORY YOU HAVE TO ENABLE IT
Take a look to custom_cfgs folder

Please dont forget you need the `bitstreams/bscan_spi_xc7a75t.bit` file
> sudo openocd -f custom_cfgs/enable-spi-bridge.cfg

# TO DOWNLOAD CURRENT SPI FIRMWARE TO A FILE
## OUTPUT FILE WILL BE `firmware_dump.bin`
> sudo openocd -f custom_cfgs/download-firmware.cfg
