# HOWTO BUILD WITH CH347 SUPPORT

Maybe you have to add extra dependencies, take a look to the other README files

```
git clone https://github.com/dowdyph0/openocd
cd openocd
./configure --enable-ch347
make
make install
sudo openocd -f target/ch347.cfg -c "transport select jtag" -f cpld/xilinx-xc7.cfg -c "init;scan_chain"
```

# ENABLE USB-SPI BRIDGE

To flash or interact with dma card internal's SPI memory you have to enable it

Take a look to `custom_cfgs` folder

Please dont forget you need the `bitstreams/bscan_spi_xc7a75t.bit` file
> sudo openocd -f custom_cfgs/enable-spi-bridge.cfg

# TO DOWNLOAD CURRENT SPI FIRMWARE TO A FILE
This is **EXPERIMENTAL** not confirmed still, it downloads the .bin file, binwalk seems to see a proper firmware but I have not tried to reupload it to he DMA card

The output file will be `firmware_dump.bin`

> sudo openocd -f custom_cfgs/download-firmware.cfg

# TO UPLOAD NEW FIRMWARE

- First you have to enable the USB-SPI bridge
- Check the `tcl/cpld/jtagspi.cfg` file for the `jtagspi_program` command
