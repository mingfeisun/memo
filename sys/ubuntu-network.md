### Motherboard networking solution 

* Mingfei Sun
* Created: 2018-06-05
* Updated: 2018-06-05

Some motherboards are designed for windows system, e.g., Asus ROG etc. When installed with Linux OS, the motherboard may fail to connect to network due to following errors:

#### NVM checksum is Not Valid
1. Download source code from [here](https://downloadcenter.intel.com/download/15817/-PCI-E-Linux-)
2. Untar and then change directory to src, find **nvm.c** file
3. Find and modify the function **e1000e_validate_nvm_checksum_generic** to 
```
s32 e1000e_validate_nvm_checksum_generic(struct e1000_hw *hw)
{
        return 0;
}
```
4. Make & install
```
cd e1000e/src
sudo make
sudo make install
```
5. Update driver
```
sudo rmmod e1000e
sudo modprobe e1000e
```
6. Start network service
```
sudo /etc/init.d/networking restart
```
7. Save settings
```
sudo update-initramfs -u
```

#### Qualcomm Atheros firmware missing
1. Download Linux firmware from [here](https://launchpad.net/ubuntu/xenial/+package/linux-firmware)
2. Install the new firmware:
```
sudo dpkg -i linux-firmware_****_all.deb
```
3. Reboot

[Read more](https://askubuntu.com/questions/607707/ath10k-installation)

#### WiFi power save mode
1. Check whether wifi power save mode is on:
```
iwconfig
# output 

wlp2s0    IEEE 802.11  ESSID:"eduroam"  
          Mode:Managed  Frequency:5.765 GHz  Access Point: 00:F8:2C:19:3A:AF   
          Bit Rate=6 Mb/s   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:9   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

enp0s31f6  no wireless extensions.

enp4s0    no wireless extensions.
```

2. The Power Management is on; To turn it off:
```
sudo vim /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

# change the wifi.powersave value to 2
wifi.powersave = 2

# values and meanings for references
# NM_SETTING_WIRELESS_POWERSAVE_DEFAULT (0): use the default value
# NM_SETTING_WIRELESS_POWERSAVE_IGNORE (1): don't touch existing setting
# NM_SETTING_WIRELESS_POWERSAVE_DISABLE (2): disable powersave
# NM_SETTING_WIRELESS_POWERSAVE_ENABLE (3): enable powersave
```

Done
[Read more](https://unix.stackexchange.com/questions/269661/how-to-turn-off-wireless-power-management-permanently)

