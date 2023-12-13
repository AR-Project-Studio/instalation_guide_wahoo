## Installation Guide for Android 14 on Walleye

### Basic requirements
1. Read through the instructions at least once before actually following them, so as to avoid any problems due to any missed steps!
2. Make sure your computer has adb and fastboot
3. Enable USB debugging on your device
4. Boot your device with the stock OS at least once and check every functionality. Make sure that you can send and receive SMS and place and receive calls (also via WiFi and LTE, if available)

### Unlocking the bootloader
1. Enable OEM unlock in the Developer options under device Settings, if present
2. Connect the device to your PC via USB.
3. On the computer, open a command prompt (on Windows) or terminal (on Linux or macOS) window, and type:
```
adb reboot bootloader
```
   "You can also boot into fastboot mode via a key combination with the device powered off, hold Volume Down + Power"

4. Once the device is in fastboot mode, verify your PC finds it by typing:
```
fastboot devices
```
   If you don’t get any output or an error:
   - on Windows: make sure the device appears in the device manager without a triangle. Try other drivers until the command above works!
   - on Linux or macOS: If you see no permissions fastboot try running fastboot as root. When the output is empty, check your USB cable and port!

5. Now type the following command to unlock the bootloader:
```
fastboot flashing unlock
```
6. If the device doesn’t automatically reboot, reboot it. It should now be unlocked
7. Since the device resets completely, you will need to re-enable USB debugging to continue

### Booting a custom recovery using fastboot
1. Download the [TWRP Recovery](blob:https://github.com/61dd1b0e-c154-410e-9989-aef7717270c9)
Simply download the latest recovery file
2. Connect your device to your PC via USB if it isn’t already
3. If your device isn’t already in fastboot mode, on the computer, open a command prompt (on Windows) or terminal (on Linux or macOS) window, and type:
```
adb reboot bootloader
```
   "You can also boot into fastboot mode via a key combination Wwith the device powered off, hold Volume Down + Power"

4. Once the device is in fastboot mode, verify your PC finds it by typing: 
```
fastboot devices
```
   If you don’t get any output or an error:
   - on Windows: make sure the device appears in the device manager without a triangle. Try other drivers until the command above works!
   - on Linux or macOS: If you see no permissions fastboot try running fastboot as root. When the output is empty, check your USB cable (preferably use a USB Type-A 2.0 one or a USB hub) and port!

5. Flash the TRWP Recovery on your device by typing
```bash
fastboot flash boot recovery_filename
```
   "replace <recovery_filename> with the actual filename!"

6. Now reboot into recovery to verify the installation. Use the menu to navigate to and to select the Recovery option.

### Pre-install instructions
Starting with Android 14, you must re-partition again your device for Android 14 to be installed. If you already repart, well you just need to flash the new repart file, no need to back to the stock partition

1. Download [productpartition-walleye-a14.zip](blob:https://github.com/7eca81be-381a-4da2-8d7f-c8983ecb65cb)
2. Sideload the .zip package:
   - On the TWRP Recovery, select ”Advance“, “Adb sideload”, then swipe to begin sideload.
   - On the computer, type adb sideload and drag to terminal the productpartition-walleye-a14.zip file then enter
3. On TWRP, return to the main menu.
4. Now tap Wipe, then Format data/factory reset and continue with the formatting process. Next reboot to recovery again
5. The last, sideload the rom like sideloading the productpartition-walleye-a14.zip on step number 2

Note: If you want to revert to the stock partition table, kindly flash the official Google factory image: [Stock Partiton - Pixel 2](https://developers.google.com/android/images#walleye)