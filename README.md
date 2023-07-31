Cudy P5 RM520N-GL modem firmware update using QFirehose via Linux

NOTE: To clarify, the Cudy P5's firmware and the Quectel RM520N-GL modem firmware inside the Cudy P5 are different.

Requirements:
1. Linux (Ubuntu in my case; It doesn't matter if via a Virtual Machine)
2. Download the zip file and extract it to your desktop
https://www.mediafire.com/file/q83yxo08tubee97/Upgrade_RM520.zip/file
3. Patience

Caution:
1. Use an Ethernet Cable and ensure that the power supply for both the PC and the modem/Router is stable (use a UPS!). If the upgrade fails, the module will not be able to recover anymore.
2. Please use the files that Cudy provides to you and not those from Quectel, as Cudy has tested the firmware provided on their end and cannot guarantee the other versions you get from other sources.


A. Preparation:
1. Download first the zip file and extract it.
2. Open terminal & change directory to the folder location (in my case it was located to /home/Desktop/user/Upgrade_RM520)
3. Copy 'qfirehose' and 'RM520NGLAAR01A07M4G_01.200.01.200.zip' to the ubuntu directory /tmp/ by runing the following command:
"chmod a+x /tmp/qfirehose
unzip /tmp/RM520NGLAAR01A07M4G_01.200.01.200.zip -d /tmp/RM520-image"
4. Change directory to /tmp/
"cd /tmp"

B. Install Beta Firmware & Modem
1. Access the web interface, go to General Settings>Cellular>APN, then disable it and save & apply the settings.
2. Go to Advanced Settings>Firmware and upgrade "P5-R21-1.16.1beta-20230731-115435-upgrade-module".
3. Once upgraded to the latest beta firmware, go back to terminal and type the following:
"./qfirehose -f /tmp/RM520-image/ -p 192.168.10.1:9008"
Note: 192.168.10.1 is the LAN IP of the router.
4. If you see at the end of the terminal 'Upgrade Module successfully.', it means the upgrade process is completed.
5. Reboot the router
6. Flash the latest stable version "P5-R21-1.15.15-20230616-112055-sysupgrade.bin"
7. After flashing the stable version, enable cellular, configure APN & confirm the module version.
8. Finish!
