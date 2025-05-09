<div align="center">

  <img src="https://files.refurbed.com/pi/lenovo-thinkcentre-m73-i4g-1604301233.jpg" alt="Image of a Lenovo ThinkCentre M73 SFF." width="60px"/>
  
  # **OpenCore 1.0.0 for the Lenovo ThinkCentre M73 SFF**

![An image of Sonoma's "About This Mac".](https://files.catbox.moe/dsg0xk.png)
  
  ## ⚠️ WARNING ⚠️
  
  **It is NOT recommended to use prebuilt OpenCore configurations. They might not work with the exact hardware of your computer, may have features enabled that you don't want, may be outdated, and are harder to diagnose. This configuration is meant to be used as a guide to help you create your own OpenCore configuration for this ThinkCentre, but it can be used as is, only at your own risk.**
  
  ## Contents
  
  [**System Specifications**](#system-specifications)
  
  [**Directions**](#directions)

  [**Updating OpenCore/macOS**](#updating-opencoremacos)

  [**Known Issues**](#known-issues)
  
  ## System Specifications
  
  | Component | Model |
  | :-: | :-: |
  | CPU | Intel Core i5-4570 @ 3.60GHz |
  | Chipset | Intel H81 Express |
  | Internal GPU | Intel HD Graphics 4600 |
  | RAM | 8GB of DDR3-1600 |
  | Storage | SAMSUNG MZ7LF120HCHP-000L1 |
  | Audio | Realtek ALC662 |
  | External Display | TEKILO TK24HG5 |
  | Ethernet | Realtek RTL8111GN |
  | Internal WiFi/Bluetooth | None |
  
  **If your system does not match these specifications, it is not guaranteed that this configuration will work for you. If you are unable to get it working, you can create an issue, and I will try to help you to the best of my ability.**

  ## Directions
  
  **Follow the steps below by going to the links provided and following the directions listed. If a step is labeled with a &#42;, that means it's optional but extremely recommended. If a step is labeled with &#42;&#42;, that means it's optional and not required.**

  | Step # | Link/Directions |
  | :-: | :-: |
  | 0.25** | Grab a supported Broadcom WiFi card [from here](https://dortania.github.io/Wireless-Buyers-Guide/types-of-wireless-card/mpcie.html), a supported Intel WiFi card (kext not included) [from here](https://openintelwireless.github.io/itlwm/Compat.html#), or a supported USB WiFi adapter (kext not included) [from here](https://github.com/chris1111/Wireless-USB-OC-Big-Sur-Adapter#%EF%B8%8E---known-working-and-testing-adapter) if you want WiFi support. |
  | 0.5 | [**For ThinkCentre M83 Tiny and M93p users**, follow this guide to increase the chances of this configuration working correctly.](/Resources/Documentation/M83andM93.md) |
  | 1 | [Creating the USB (Do not move the EFI folder. ProperTree is not needed.)](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/#making-the-installer) |
  | 2 | Move the "EFI" folder from this repository to the "EFI" partition on macOS, to the root of your USB drive on Windows, or to the "OPENCORE" partition on Linux. Make sure to move the whole folder itself and not just the files inside the folder. |
  | 3 | [Modify your BIOS settings according to this document. Skip "VT-d" if you do not see it in your BIOS.](/Resources/Documentation/BIOSSettings.md) |
  | 4 | [Installation Process (Skip "Double checking your work". Check "OpenCore Multiboot Guide" if you want to multiboot.)](https://dortania.github.io/OpenCore-Install-Guide/installation/installation-process.html#booting-the-opencore-usb) |
  | 5 | [**For Ventura and Sonoma users**, use OpenCore Legacy Patcher to get graphics acceleration and WiFi connectivity.](/Resources/Documentation/OCLP.md) |
  | 6* | [Moving OpenCore from USB to macOS Drive (Skip the "Legacy" part at the bottom)](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html) |
  | 7* | [Fixing iMessage and other services with OpenCore (This is extremely recommended even if you don't use iServices because otherwise, you will have a generic serial number, which isn't a great idea.)](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html) |
  | 8** | [**For Big Sur and Monterey users**, modify the OpenCore configuration to improve security.](/Resources/Documentation/Security.md) |

  ## Updating OpenCore/macOS
  
  ### Updating OpenCore with a newer version of this configuration
  **If you want to update OpenCore with a newer version of this configuration, just download the new EFI folder, mount the EFI partition, and copy the folder to the partition. Note, if you've made any changes to the configuration, make sure to remember them or save them somewhere because any changes made will be overwritten.**

  ### Updating OpenCore/macOS manually
  **If you want to update OpenCore manually, you can follow [this guide](https://dortania.github.io/OpenCore-Post-Install/universal/update.html#updating-opencore) (harder to follow, but recommended and tells you how to update macOS), or follow [this guide](https://www.insanelymac.com/forum/topic/347035-guide-updating-and-maintaining-opencore-new-method/) (easier to follow, but not recommended.) If you want to update macOS 13 Ventura or macOS 14 Sonoma, follow [this guide here.](/Resources/Documentation/OCLP.md#before-updating-macos)**

  ## Known Issues

  ### Unable to boot from Internal Drive
  **Depending on System, Some PC causes unable to boot from Hard Drive. You'll have to use USB for booting. (If it's working on Updated BIOS, Let me know.)**

  ### AMFI
  **AMFI (Apple Mobile File Integrity is _Disabled_ or causes bootlooping.**

  ### OpenCore Legacy Patcher Issues
  **Because macOS 13 Ventura and macOS 14 Sonoma do not officially support the hardware featured in this ThinkCentre, we have to use a tool called "OpenCore Legacy Patcher" to apply patches that allow us to use Ventura and Sonoma normally. Sadly, these patches do have some minor issues. To check the issues that affect this ThinkCentre, check [this link](https://github.com/dortania/OpenCore-Legacy-Patcher/issues/1008/) and look for "Haswell" in "Known Issues". As mentioned before, these bugs are quite minor and will not affect most people.**

  ### No VGA Output
  **Due to macOS not officially supporting VGA, you will not be able to output the macOS user interface via the VGA port featured on the ThinkCentre. At the moment, this is currently impossible to fix.**

  ### Monterey 12.3+ crashes during setup on the HD4400
  **With the HD4400, Monterey 12.3 or newer crashes during the "Migration Assistant" part of the setup. Sometimes, you can get past the screen, but it'll freeze later. This issue can only be fixed by upgrading your CPU to one with an HD4600 iGPU. It is unknown if this happens in Ventura or Sonoma.**

  ### HD4400 Glitching and Freezing
  **The HD4400 has many issues in macOS. For example, some icons may be missing (image below), some random freezes may happen, icons may get replaced, and possibly more. In newer versions of macOS, this can make the system almost unusable. This is impossible to fix at the moment, and the only thing you can do is upgrade your CPU to one with an HD4600 iGPU.**

  ![An image showing an example of icons going missing in macOS.](/Resources/Images/Missing%20Icons/DarkMissingIcons.png#gh-dark-mode-only) ![An image showing an example of icons going missing in macOS.](/Resources/Images/Missing%20Icons/LightMissingIcons.png#gh-light-mode-only)
  
  [**Jump to Top**](#opencore-100-for-the-lenovo-thinkcentre-m73-tiny)

</div>
