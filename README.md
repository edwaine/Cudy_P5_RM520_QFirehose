# Cudy P5 RM520N-GL modem firmware update using QFirehose via Linux

NOTE: To clarify, the Cudy P5's firmware and the Quectel RM520N-GL modem firmware inside the Cudy P5 are different.

Requirements:
1. Linux (Ubuntu in my case; It doesn't matter if via a Virtual Machine)
2. Download the zip file and extract it to your desktop
   [https://www.mediafire.com/file/q83yxo08tubee97/Upgrade_RM520.zip/file](https://www.mediafire.com/file/8h45jt668wlxx06/Upgrade_RM520.zip/file)
3. Download the latest Quectel Firmware
   [https://www.mediafire.com/folder/l0ix2ptyq8vhz/Quectel_RM520N-GL_Firmware](https://www.mediafire.com/folder/l0ix2ptyq8vhz/Quectel_RM520N-GL_Firmware)
4. Patience

Caution:
1. Use an Ethernet Cable and ensure that the power supply for both the PC and the modem/Router is stable (use a UPS!). If the upgrade fails, the module will not be able to recover.
2. Please use the files that Cudy provides to you and not those from Quectel, as Cudy has tested the firmware provided on their end and cannot guarantee the other versions you get from other sources.


A. Preparation for Modem:
1. Login to Cudy.net
2. Go to General Settings
3. Under Cellular>APN, Toggle to disable cellular.

B. Preparation for Ubuntu:
1. Download the zip file first and extract it.
2. Open the terminal, type "sudo -s" and enter the password.
3. Change directory to the folder location (in my case, it was located at /home/"Username Here"/Desktop/Upgrade_RM520)
4. Copy "qfirehose" and "the latest Quectel Firmware" to the Ubuntu directory /tmp/ by running the following command:
"chmod a+x /tmp/qfirehose"
"unzip /tmp/Latest_Quectel_Firmware_Here.zip -d /tmp/RM520-image"
5. Change directory to /tmp/
"cd /tmp"

C. Install Beta Firmware and Modem
1. Access the web interface, go to General Settings>Cellular>APN, disable it, and save and apply the settings.
2. Go to Advanced Settings>Firmware and upgrade "P5-R21-1.16.1beta-20230731-115435-upgrade-module".
3. Once upgraded to the latest beta firmware, go back to the terminal and type the following:
"./qfirehose -f /tmp/RM520-image/ -p 192.168.10.1:9008"
Note: 192.168.10.1 is the LAN IP of the router.
4. If you see at the end of the terminal "Upgrade Module successfully", it means the upgrade process is completed.
5. Reboot the router
6. Flash the latest stable version, "P5-R21-1.15.15-20230616-112055-sysupgrade.bin"
7. After flashing the stable version, enable cellular, configure APN & confirm the module version.
8. Finish!

Reference: https://cnquectel-my.sharepoint.com/:b:/g/personal/ae-fae_quectel_com/EY86kgo8vwxEnbr6lF7KN-sBhjTFl8x8Ne-ImXINJY2dNA?e=4QgEC6
