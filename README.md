# DELL-XPS9560
CLOVER FOR MAC CATALINA
Welcome to my XPS 15 9560 guide. This guide should work for most hardware configurations, but here is my configuration:

CPU: i5-7300HQ @ 2.5GHz
8GB RAM
Nvidia GTX 1050 / Intel HD 630
1080p IPS display (See edit in pre-install for 4k display)
1TB Samsung NVMe SSD
Broadcom BCM94352Z Dell DW1560 Wifi + BT card

 What should work:
Audio
Brightness + volume controls
HDMI + Thunderbolt 3 (TB3 at least works as a display output, not sure about other functionality)
Wi-Fi/Bluetooth assuming you swapped your Wi-Fi card.
What doesn't work:
SD card reader
Fingerprint reader
dGPU (Nvidia Optimus not supported on MacOS)
 Let's get started!  

Pre-install:  

First make sure your BIOS settings are in good shape. There are guides all over on correct BIOS settings to use.  

Next, you will need the latest Download of MacOS Catalina. If you can’t download the full Catalina installer from the Mac App Store, download it with the Catalina Patcher tool here. It should be about 8gb in size.

  You will also need a minimum 8gb flash drive formatted in Mac OS Extended (Journaled) on GPT format.   You can use this command to format your drive:

Code:
diskutil partitionDisk /dev/*YOUR DISK* GPT JHFS+ MojaveInstallUSB 0b
Next you will need to install the Catalina Installer to the drive. The command is:

Code:
sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/ MojaveInstallUSB
Next, download and install the latest version of clover from Github.
Make sure you choose to install it to the USB!
Install for UEFI booting only
Install Clover to the ESP
If it fails, make sure your USB is properly formatted.

Next, download my CLOVER folder below. Before you replace the CLOVER folder in the /EFI/efi, copy out the /EFI/efi/CLOVER/CLOVERX64.efi file onto your desktop. Then replace the CLOVER folder with the one you downloaded and then copy back the CLOVERX64.efi into the CLOVER folder.

Now you will need to download the kexts. A problem with a lot of guides (including my own) future-proof wise is that having old kexts/Clover builds in their downloads makes the chances of compatibility with future versions of MacOS very small.

Download Clover Configurator Here (https://mackie100projects.altervista.org/download-clover-configurator/) and click on the kext installer at the bottom left. Make sure it is installing kexts to the EFI partition on the USB drive, and also that it is placing them in the kexts/other folder and not 10.6. The installer will scan your kexts to see if an update is available. If an update is available, update them! Sometimes in my experience I have found that some kexts may not want to install through this installer. If this is the case just google the kext and install it manually.

 Next place the Clover installer and Clover Configurator your downloaded onto your non-EFI partition on your USB. You will use this to make your laptop bootable without the USB drive.  

Now you are ready to install! Boot into the drive by pressing f12 while booting. Select the UEFI version of the USB if available.  

Installation:  

Select the MacOS Install partition at the clover boot panel.  At the installer screen, open disk utility through the top right menu bar. This is where you will format your drive as APFS  

WARNING: If you intend to dual/triple/whatever boot your system, I would create the partitions in Windows FIRST, and then use Disk Utility to format the partition you want to install on. This is how I successfully Dual-booted with my existing Win10 install. If you don't have windows installed already or want to wipe it you can format and partition from DU.  

Once your partition is formatted as APFS, go back to the installer screen and install to the drive.  After that is done, reboot (to your USB again!) and select "Boot *drive name* from USB" or whatever your equivalent is. Complete installation as normal.  

Post-installation:  

Now that you are on the desktop, open the USB and drag the Clover Installer and Clover Configurator onto the Desktop.   Move Clover Configurator to your Applications folder.  

Launch Clover installer and install Clover to your main drive.  

Next, open Clover Configurator and use it to mount your main drive's & USB drive's EFI partitions. Drag your CLOVER folder from within the EFI folder on your USB installer to the EFI folder on your main drive.  

At this point, you should have a fully functioning hackintosh! If there is an issue with this guide or the configs I attached HMU and I'll do my best to fix them.
  If the Dell dock does not work, try changing the SMBIOS to Macbook 9,1.
  If your graphics aren't working properly, try changing your intelGFX deviceID to 0x59120000.  
For Wifi/BT issues, try disabling Power Nap，`System Preferences` -> `Energy Saver` disable all `Power Nap` options, and disabling `Wake for Wi-Fi network access` option and also try disabling Wake for Bluetooth, `System Preferences` -> `Bluetooth` -> `Advanced` disable all options.
Edit 1: Cleaned up the Clover folder.
