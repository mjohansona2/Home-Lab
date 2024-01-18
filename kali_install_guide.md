
# Importing Kali Linux from Official Sources

## Introduction
This guide provides step-by-step instructions on how to import Kali Linux into a Virtual Machine (VM) environment using official sources.

## Prerequisites
- Ensure you have a stable internet connection for downloading files.
- Install VirtualBox on your system.

## Steps to Import Kali Linux

### 1. Download Kali Linux VM Image
- Visit the official Kali Linux website: [Kali Linux Downloads](https://kali.org/get-kali/).
- Navigate to the **Virtual Machines** section.
- Click on the **Download** icon next to the desired VM image.
  - Note: The file is large and the download time will vary based on your internet speed.

### 2. Prepare the Downloaded Files
- After downloading, locate the `.7z` file on your system.

![kali1](https://github.com/mjohansona2/Home-Lab/assets/6199686/091cb1a9-cf19-4ac8-b4f0-5b18cb89ebf3)

- Extract the `.7z` file to unarchive the `.vbox` and `.vdi` files.

![kali2](https://github.com/mjohansona2/Home-Lab/assets/6199686/d92f0027-fbbf-433a-a171-842377d2a396)
![kali3](https://github.com/mjohansona2/Home-Lab/assets/6199686/f865cfdf-f58e-4c01-92dd-3fc570d040dc)
![kali4](https://github.com/mjohansona2/Home-Lab/assets/6199686/be06d698-c992-46fd-9429-6709fe312acf)

- Rename the folder containing the VM files for easier identification.

![kali5](https://github.com/mjohansona2/Home-Lab/assets/6199686/7c2d9534-3dea-490a-89b4-08720e8f5d77)

### 3. Transfer Files to VirtualBox Directory
- Move the extracted folder to where your virtual machines are stored.

### 4. Set Up Kali Linux in VirtualBox
- Open VirtualBox.
- Use the `Machine` > `Add` option in the menu to browse and select the `.vbox` file from the pasted files.

![kali6](https://github.com/mjohansona2/Home-Lab/assets/6199686/de828efe-1030-46e0-a100-4158dca28eb6)

- Click on `Settings` > `Network`
- Update Adapter1 to `Internal Network` and `cyber-range-lan`

![kali-setting1](https://github.com/mjohansona2/Home-Lab/assets/6199686/c90810bb-06b4-4481-ae59-4b5dc597d4ef)

- Make sure the pfSense vm is running and boot the Kali VM
- Default login for Kali is `kali kali`
- You can verify it got its ip address from pfSense by opening a shell and running `ip a`

![kali7](https://github.com/mjohansona2/Home-Lab/assets/6199686/36646575-e8e6-47e7-a6d2-0d39e6a1914f)

## Conclusion
You have now successfully imported Kali Linux into your VirtualBox environment.

