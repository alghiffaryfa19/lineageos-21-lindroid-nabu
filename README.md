# Install Lineage OS 21 with Lindroid (Linux on Android) Xiaomi Pad 5 (NABU)

### Flashing nabu via recovery mode.

> This guide assumes you know what you are doing and you have latest platform tools installed along with drivers.

* Download all files from [Here](https://drive.google.com/drive/folders/1iZrJMFk_ekmWKlzR0b3SOqTG0eoVGKpg?usp=sharing)


* flash or boot to TWRP (you can find guide from forum or etc)

#### In recovery do the following. (You should see LineageOS logo if not then something isn't right)
> Touchscreen takes a little bit of time to probe sometimes so give it 20 seconds if you see that touchscreen is not working.

1: Tap Factory Reset, then Format data / factory reset and continue with the formatting process. This will remove encryption and delete all files stored in the internal storage.

2: Return to the main menu.

3: Sideload the LineageOS .zip package but do not reboot before you read/followed the rest of the instructions!
* On the device, select “Apply Update”, then “Apply from ADB” to begin sideload.
* On the host machine, sideload the package using: adb sideload filename.zip.
> Normally, adb will report Total xfer: 1.00x, but in some cases, even if the process succeeds the output will stop at 47% and report adb: failed to read command: Success. In some cases it will report adb: failed to read command: No error or adb: failed to read command: Undefined error: 0 which is fine.

4: reboot to bootloader
* Once in fastboot flash the artifacts that you downloaded, execute the following commands
* boot
  
`fastboot flash boot_a boot.img`

`fastboot flash boot_b boot.img`

* dtbo
  
`fastboot flash dtbo_a dtbo.img`

`fastboot flash dtbo_b dtbo.img`

* vendor_boot
  
`fastboot flash vendor_boot_a vendor_boot.img`

`fastboot flash vendor_boot_b vendor_boot.img`

> Reboot device.

`fastboot reboot`

#### Configure your device
1: Download lindroid rootfs [Here](https://lindroid.org/lindroid.tar.gz).
2: enable usb debugging and rooted debugging in developer options.
3: open lindroid app and kill from recent apps.
4: rename downloaded rootfs to rootfs.tar.gz and push with adb.
`adb push rootfs.tar.gz /data/data/org.lindroid.ui/files/`
5: enter adb shell.
`adb shell`
6: execute this command.
`lxc_create default -t lindroid -- -f /dev/fd/4 "4</data/data/org.lindroid.ui/files/rootfs.tar.gz"`
7: after completing the command, open lindroid app and click "default", please wait until boot into linux, the default password is "lindroid".
