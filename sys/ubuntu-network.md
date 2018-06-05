### Motherboard networking solution 

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
2. install as follows:
```
sudo dpkg -i linux-firmware_****_all.deb
```
3. Reboot
[Read more](https://askubuntu.com/questions/607707/ath10k-installation)
