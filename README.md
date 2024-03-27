# Acer Nitro V 15
Downgrading the BIOS, Panic BIOS rescue, Advanced **BIOS settings** unlock + fixes for common issues.

# Downgrading the BIOS

```diff
- Proceed with caution. There's always the possibility that your device might get bricked.
```

> The device must be plugged to the AC Adapter and is charging.

### Steps
1.    Download the old BIOS version from the Acer support website, extract the ```.zip``` file and run the setup executable.
2.    You will get an error, keep the window open and don't press anything.
3.    Hit the **Windows Key** and the **R** key to open up the **Run window**. Type in the run dialog ```temp``` and press **OK**.
4.    Click on **View tab** and Enable the option to **Show Hidden Files, folders and drives**. Click **Okay**.
5.    Look for a folder starting with the name ``7z`` and ends with ``.tmp``
7.    Copy the folder to desktop or any other perferable place then proceed to open up the folder.
9.    Inside the folder, look for a file with the name ```platform.ini```, right click it and edit it using **Notepad** or any other text editor of choice.
10.   Press ``CTRL+F`` on your keyboard and look for ```[Bios_Version_Check]```
11.   There will be a flag value assigned to it, change it to 0. ```flag=0```
12.   Then proceed to run the executable file in folder with the name ```H2OFFT-W.exe```.
13. After downgrading, head into **Device Manager** and uninstall the previous **BIOS firmware** to prevent auto-update right after downgrading.

## Why should you downgrade the BIOS?
Acer BIOS updates suck. They end up tanking the performance of your device and at times disabling core features like **LCD Overdrive**. Do not update to BIOS version 1.09, it disables **LCD Overdrive** feature in NitroSense.

# Panic BIOS rescue
In the event that you might have bricked your device (eg. POST w/ Black screen) as a result of downgrading your BIOS or messing around with the Advanced BIOS settings, there's no need to panic as you can save your device.
### Requirements
1. Another PC/Laptop.
2. A USB stick, 4GB or more.
### Steps
1. Download the appropriate BIOS version from the Acer support website, extract the ```.zip``` file.
2. Right click the executable ```.exe``` file, and extract it using **7zip**. If this does not work, follow the steps **2 - 7** from **Downgrading the BIOS** section.
3. Look for a file with the extension ```.fd``` there should only be one file with such extension.
4. Now format the USB stick with the filesystem **FAT32**.
5. Drag the ```.fd``` file into the USB stick.
6. Now, make sure that the device (the one that's bricked) is turned off and is plugged in to the power cable.
7. Insert the USB stick into the device. Now hold the **function key** ```Fn``` and the escape key ```Esc``` and press the power button. Let go off the keys once the Fans start kicking in.
8. If the power light flashes, that means that the BIOS is being written to, **DO NOT TURN OFF OR INTERUPT** the device.
9. The device will shutdown once complete and it will take longer than usual to boot but that's okay.


# Advanced BIOS settings

```diff
- Changing the wrong settings WILL brick your device.
- While it is relatively safe, modifying the settings is NOT so proceed with caution.
```

### Steps
**Preparing the USB stick.**
1. Grab a USB stick. Convert it to **GPT** partition scheme and format it as FAT32. [How to convert a USB stick to GPT partition scheme](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-an-mbr-disk-into-a-gpt-disk)

2. Download SREP from [Smokeless Github Repo](https://github.com/SmokelessCPUv2/SmokelessRuntimeEFIPatcher/releases) - <https://github.com/SmokelessCPUv2/SmokelessRuntimeEFIPatcher/releases>
3. Extract the contents of the zip file into the USB stick.
4. Download pre-made patch for **AN16-51(17-51)** or **AN16-41(17-41)** from [Sweet Kittens repo](https://github.com/Maxinator500/SREP-Patches) - <https://github.com/Maxinator500/SREP-Patches>  (right click on RAW and save as)
5. Rename it to ``SREP_Config.cfg`` and move it to the root of the usb.

Your USB content/files should look like the screenshot below.

![image](https://github.com/vindarts/acer-nitro-v-15/assets/115871738/62ed61a8-4c79-4044-9d4d-8dc0bc8d8c12)

### Booting into the Advanced BIOS 
1. Press the ```F2``` button back and forth when laptop is starting up to access the BIOS.
2. Set an Administrator/Supervisor password (Set it to **0000** OR anything of your choice. DON'T FORGET IT.)
3. Disable **Secure Boot**. (Ensure Bitlocker is not turned off.)
4. Change boot order so that the USB stick has the first priority.
5. Save and Exit

Now it will boot to USB stick and you will be able to access the Advanced Settings as long as the USB stick is connected. Be warned, do not modify any settings without knowing what it does. It can brick the device. The settings you change will be saved even after you unplug the USB stick. In the event that you do brick your device, refer to **Panic BIOS rescue** section. You will see unlocked BIOS only when you boot from the USB stick. Regular F2 will present you with normal locked BIOS.
