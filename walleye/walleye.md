![Installation Guide For Android 14](https://github.com/Google-Pixel2-2XL/instalation_guide_wahoo/blob/main/AR-Project%20Banner.png)

## Installation Guide for Android 14 on Google Pixel 2 (Walleye)

### Basic requirements
> [!Important]
> * Read through the instructions at least once before actually following them, so as to avoid any problems due to any missed steps!
> * Make sure your computer has adb and fastboot
> * Enable USB debugging on your device
> * Boot your device with the stock OS at least once and check every functionality. Make sure that you can send and receive SMS and place and receive calls (also via WiFi and LTE, if available)

### Unlocking the bootloader
1. Enable OEM unlock in the Developer options under device Settings, if present
2. Connect the device to your PC via USB
3. On the computer, open a command prompt (on Windows) or terminal (on Linux or macOS) window, and type:
```
adb reboot bootloader
```
> [!Tip]
> You can also boot into fastboot mode by using a key combination while the device is powered off: hold the Volume Down + Power buttons.
4. Once the device is in fastboot mode, verify your PC finds it by typing:
```
fastboot devices
```
> [!Tip]
> If you get any output or an error:
> * on Windows: make sure the device appears in the device manager without a triangle. Try other drivers until the command above works!
> * on Linux or macOS: If you see no permissions fastboot try running fastboot as root. When the output is empty, check your USB cable and port!
5. Now type the following command to unlock the bootloader:
```
fastboot flashing unlock
```
> [!Note]
> * If the device doesn’t automatically reboot, reboot it. It should now be unlocked.
> * Since the device resets completely, you will need to re-enable USB debugging to continue.

### Repartition
> [!Warning]
> Specifically for the build provided by AR Project Studio, you must repartition your device again. If you have already repartitioned using the PixelExperience partition, you only need to flash the new repart file, there’s no need to revert to the stock partition. However, if you want a completely clean setup, you can revert to the stock partition first and then repartition again.

1. Download [TWRP Recovery](https://github.com/Google-Pixel2-2XL/instalation_guide_wahoo/raw/evolution-x/walleye/twrp/twrp-3.3.0-0-walleye.img)
2. Download [Partition A14 Pixel 2](https://github.com/Google-Pixel2-2XL/instalation_guide_wahoo/raw/evolution-x/walleye/repart/partition14-walleye.zip)
3. Connect your device to your PC via USB if it isn’t already.
4. If your device isn’t already in fastboot mode, on the computer, open a command prompt (on Windows) or terminal (on Linux or macOS) window, and type:
```
adb reboot bootloader
```
5. Once the device is in fastboot mode, verify your PC finds it by typing: 
```
fastboot devices
```
6. Flash the TWRP Recovery on your device by typing:
```
fastboot flash boot <recovery_filename>.img
```
> [!Note]
> Replace <recovery_filename> with the actual filename, or simply drag and drop the file into the terminal.
7. Now reboot into recovery
8. Sideload the new partition file by typing:
```
adb sideload <partition_filename>.zip
```
> [!Note]
> Replace <partition_filename> with the actual filename or just drag & drop the file to the terminal
9. In TWRP Recovery, select "Advanced," then "ADB Sideload," and swipe to begin the sideload process.
> [!Important]
> * After the flashing is complete, in TWRP, select "Return to the main menu."
> * Select "Wipe," then select "Format Data/Factory Reset" and proceed with the formatting

## Flashing

### Clean flash
1. Reboot into bootloader by typing:
```
adb reboot bootloader
```
2. Wipe data by typing:
```
fastboot -w
```
3. Flash the AOSP Recovery (boot.img)
4. Reboot into recovery
5. In recovery, select "Apply Update"
5. Sideload the ROM by typing:
```
adb sideload <ROM_filename>.zip
```
> [!Note]
> Replace <recovery_filename> with the actual filename, or simply drag and drop the file into the terminal.
6. Reboot system

### Dirty flash
1. Reboot into recovery by typing:
```
adb reboot recovery
```
2. In recovery select "Apply Update"
2. Sideload the ROM by typing
```
adb sideload <ROM_filename>.zip
```
> [!Note]
> Replace <ROM_filename> with the actual filename, or simply drag the file into the terminal.
3. Reboot system

> [!Important]
> If you want to back to the stock partition table, kindly flash the official Google factory image: [Stock Partiton - Pixel 2](https://developers.google.com/android/images#walleye)

## Credit:
   - PixelBoot
   - Lanchon's Flashize
