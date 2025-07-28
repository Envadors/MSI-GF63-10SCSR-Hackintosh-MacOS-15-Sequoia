# MSI-GF63-10SCSR-Hackintosh-MacOS-15-Sequoia-OpenCore
This Repository Has A EFI That Uses Opencore 1.5 And Is For MacOS Sequoia

![OpenCore](https://img.shields.io/badge/OpenCore-1.2-Blue.svg)
![macOSver](https://img.shields.io/badge/macOS-15-Green.svg)

![51Rf3zw4rIL _AC_SL1000___1_-removebg-preview](https://github.com/Envadors/Msi-Gf63-10scsr-Sonoma-Hackintosh-EFI/assets/91122426/c464e44d-02e7-4c8d-baf0-890be9126e7c)

----------------------------------------------------------------------------------------------------

### ⚠️ Disclaimer:
- I Recommend Learning The Basics Of Hackintosh So You Can Update It Or Trouble Shoot If Anything Goes Wrong
- This EFI may not be constantly updated to the latest version of opencore especially if no major changes are made
- Please read the whole readme before proceeding

------------------------------------------------------------------------------------------------------

- [EFI For macOS Sequoia](https://mega.nz/file/qyYFzQgZ#jt1jlzu5tYLbBmASSK5_78fykgajI1BDZV8K30W0hwE)
- [EFI For macOS Sonoma](https://github.com/Envadors/Msi-Gf63-10scsr-Sonoma-Hackintosh-EFI)
- [EFI Link For macOS Ventura Until Big Sur](https://github.com/Forte500/Hackintosh-msi-GF65-10UE)


------------------------------------------------------------------------------------------------------

### ✅️ What works</strong></summary>

- iGPU acceleration Intel UHD 630 2048 MB
- Sleep
- Power management
- Audio (speaker, microphone, headphone jack)
- Battery percentage
- USB ports
- Display Brightness
- Wifi
- iMessage
- Dual Boot with windows 10 & 11
- Keyboard
- volume FN keys
- Trackpad
- Internal camera
- Ethernet port
- Continuity: Handoff & Universal clipboard
- AirPlay: `iPad -> Mac` & `Mac -> TV`
- Sidecar wired
- Sidecar wireless with broadcom card only
- Brightness
- Bluetooth
### ❌️ What doesn't work
- Video output over USB-C (Has Not Been Tested)
- Apple Watch Unlock, Universal Control, Instant Hotspot with broadcom card
- HDMI Since The Port Is Wired To NVIDIA.
- NVIDIA Graphics Card As MacOS Never Nativity Supported It.

### ⚠️ Known issues
- Wireless sidecar may lag (tested with BCM94360NG & iPad 6 ios 15.1)

⚠️ You do not need to modify the EFI to get it to run! However if you also want to get icloud running you will need to
generate a simbios for it which I listed the steps in  the bottom ⚠️

### 💻 My Hardware
| Component       |  Brand/info                                                             |
|-----------------|-------------------------------------------------------------------------|                                   
| CPU	             | Intel Core i7 10th Gen (also compatible with Intel Core i5 10th Gen)   |
| Graphics Card	   | NVIDIA GTX 1650 TI with Max Q Design (disabled on MacOS)               |
| RAM	             | 16GB                                                                   |
| Storage	         | 1.5TB                                                                  |
| WiFi Card        | Intel Wi-Fi 6 AX201                                                    |
| Bluetooth	       | Integrated with Wi-Fi card                                             |
| Laptop Keyboard	 | VoodooPS2                                                              |
| Touchpad	        | VoodooPS2                                                              |

❤️ Credits to Forte500 on Reddit for providing the original EFI configuration compatible with both Ventura and Monterey, which I then modified and optimized for Sonoma. The Sequoia EFI, however, was developed entirely by me from the ground up, with no external sources or pre-existing configurations used. ❤️



## 🛠 UEFI - Bios Settings
<details>
<summary><strong>UEFI Custom Hackintosh Settingse</strong></summary>
   <br>
   
**Update Your BIOS To Version E16R4IMS.10B Which Was Released On 2021-01-20**
  
**Firstly Unlock hidden BIOS Settings by pressing `right shift + right Ctrl + left alt + F2`**

**Advanced TAB**
- `Power & Performance > CPU-Power Management Control > Configure CPU Lock Options > CFG lock`: must be **Disabled**
- `Intel Virtualization Technology` & `VT-d` both enabled
- `System Agent (SA) Configuration > Graphics Configuration > DVMT Pre-Allocated`: must be **64M**
- `USB Configuration > XHCI Hand-off`: must be **Enabled**
- `Intel(R) Speed Shift Technology`: must be **Enabled**

**Boot TAB**
- `Fast Boot`: **Disabled**

**Security TAB**
- `Secure Boot > Secure Boot Support`: must be **Disabled**

</details>

## 🛠 Post-install

<details>
<summary><strong>Copy EFI to the internal drive</strong></summary>
<br>

1. Open terminal. Type `sudo diskutil mountdisk disk0s1` (disk0s1 corresponds to the EFI partition of the internal disk)  
2. Open Finder and copy the entire EFI folder from your USB to the root disk's EFI partition.  
3. Unplug the USB device and reboot your laptop, while rebooting hold down `F10 Or F11` to access the boot menu.  
4. Boot from `Kingstone-579420` (or your SSD's name).  
5. To check that everything has gone well repeat `step 3` and look for a new entry called `OpenCore`.  
6. Now you can boot macOS without your USB device. ✅️  

</details>

## 🛠 SMBIOS

<details>
<summary><strong>Make A Serial Number To Get iCloud Running</strong></summary>
<br>

1. Prepare your config.plist which you've made.
2. Download or clone the whole repo of [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).
3. Open the folder and open GenSMBIOS.bat \(on Windows\) or right-click open GenSMBIOS.command \(on macOS\)
4. Enter 1 and enter. \(for update/install MacSerial\)
5. Then enter 2 and enter.
6. Drag and drop your config.plist and press enter.
7. Y.
8. Enter 3 and enter.
9. Enter the SMBIOS you want to generate and enter the number of SMBIOS amount. Press enter. **For AMD System,** here is the list of SMBIOS recommended from the most to the least: - _**iMacPro1,1**_ \(most recommended\) - _**iMac14,2**_ ****\(also recommended\) - MacPro6,1 \(a little bit old but it works\) - MacPro5,1 \(outdated and already lost support on Catalina\) - Other SMBIOS \(not recommended as they might cause problems\)
10. The first SMBIOS will be flushed into your chosen config.plist.
11. Icloud Services Should Work Now And Enjoy Your Hackintosh 👍.

</details>

## 🛠 Enable WI-FI
<details>
<summary>OCLP Method (The Only Method For This EFI)</strong></summary>
  <br>
  
1. Download Open Core Legacy Patcher from [here](https://github.com/dortania/Opencore-Legacy-Patcher/releases/2.4.0).
2. Open the .dmg, press I Agree, and let it install.
3. Open Finder > Applications and launch OpenCore Legacy Patcher.
4. Click Post-Install Root Patch, and you should see Modern Wireless in the list.
5. Press Start Root Patching, then enter your password if asked.
6. Once it's done, reboot your system.
7. Wi-Fi should now be working natively ✅.


  
</details>

## 🛠 Enable Trackpad Click

<details>
<summary><strong>Customize Via Settings</strong></summary>
<br>

1. Go Into Settings, Then Into Trackpad.
2. Disable Force Click And Haptic Feedback
3. You can now lightly tap the trackpad to press. Hard pressing Wont Work.
   </details>
