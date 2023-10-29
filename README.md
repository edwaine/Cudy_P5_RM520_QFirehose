# Cudy P5 RM520N-GL modem firmware update using QFirehose via Windows Subsystem for Linux and Ubuntu

NOTE: To clarify, the Cudy P5's firmware and the Quectel RM520N-GL modem firmware inside the Cudy P5 are different.

Requirements:

      1. Enable the following by going to "Windows Features": Hyper-V, Virtual Machine Platform, Windows Hypervisor Platform and Windows Subsystem for Linux
      2. Update first your WSL using Windows Update
      3. Download the Ubuntu app from the Microsoft Store:
      https://www.microsoft.com/p/ubuntu/9pdxgncfsczv
      4. Or use Ubuntu on a physical device or a Virtual Machine (VMWare or other virtual machine apps)
      5. Download the zip file and extract it to your desktop
      https://www.mediafire.com/file/8h45jt668wlxx06/Upgrade_RM520.zip/file
      6. Download the latest Quectel Firmware
      https://www.mediafire.com/folder/l0ix2ptyq8vhz/Quectel_RM520N-GL_Firmware
      7. Patience

Caution:

      1. Use an Ethernet cable and ensure that the power supply for both the PC and the modem/router is stable (use a UPS!). If the upgrade fails, the module will not be able to recover.
      2. Please use the files that Cudy provides to you and not those from Quectel, as Cudy has tested the firmware provided on their end and cannot guarantee the other versions you get from other sources.

A. Preparation for Modem:
      
      1. Login to Cudy.net
      2. Go to General Settings
      3. Under Cellular>APN, toggle to disable cellular.

B. Preparation for Windows:

      1. Download "Upgrade_RM520.zip" and extract it to your desktop. Download "the latest Quectel Firmware" and place it on your desktop.
      2. Copy "QFirehose" to the Ubuntu directory /tmp/ by going to "Linux>Ubuntu>tmp"
      3. Create a new Folder named "RM520-image" on the /tmp/ folder and extract "the latest Quectel Firmware" on the "RM520-image" folder 
      4. Open the Ubuntu terminal, type "sudo -s" and enter the password.
      5. Change the directory location to /tmp/ by typing "cd /tmp"
      6. Change QFirehose file permissions by typing "chmod ugo+x QFirehose"
      7. Test if QFirehose is accessible by typing "./QFirehose -p"
      8. If step 7 worked, proceed to the next step

C. Preparation for Ubuntu:

      1. Download "Upgrade_RM520.zip" and extract it to your desktop. Download "the latest Quectel Firmware" and place it on your desktop.
      2. Copy "QFirehose" to the Ubuntu directory /tmp/ by going to "Files App>Other Locations>Ubuntu>tmp"
      3. Create a new Folder named "RM520-image" on the /tmp/ folder and extract "the latest Quectel Firmware" on the "RM520-image" folder 
      4. Open the terminal, type "sudo -s" and enter the password.
      5. Change the directory location to /tmp/ by typing "cd /tmp"
      6. Change QFirehose file permissions by typing "chmod ugo+x QFirehose"
      7. Test if QFirehose is accessible by typing "./QFirehose -p"
      8. If step 7 worked, proceed to the next step
      
D. Install Beta Firmware and Modem

      1. Go to Advanced Settings>Firmware and upgrade "P5-R21-1.16.1beta-20230731-115435-upgrade-module".
      2. Once upgraded to the latest beta firmware, go back to the Ubuntu terminal and type the following:
      "./QFirehose -f /tmp/RM520-image/ -p 192.168.10.1:9008"
      Note: 192.168.10.1 is the default LAN IP of the router. Change this if you modify your DHCP server.
      3. If you see at the end of the terminal "Upgrade Module successfully", it means the upgrade process has been completed.
      4. Reboot the router
      5. Flash the latest stable version, "P5-R21-1.15.15-20230616-112055-sysupgrade.bin"
      6. After flashing the stable version, enable cellular, configure APN, and confirm the module version.
      7. Finish!

NOTE:
      1.16.1 beta will only enable QFirehose on Cudy P5's side. Cellular will never work. In order for you to use cellular, revert back to the latest stable version.

Reference: https://cnquectel-my.sharepoint.com/:b:/g/personal/ae-fae_quectel_com/EY86kgo8vwxEnbr6lF7KN-sBhjTFl8x8Ne-ImXINJY2dNA?e=4QgEC6
