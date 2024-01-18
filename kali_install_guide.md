
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
- Extract the `.7z` file to unarchive the `.vbox` and `.vdi` files.
- Rename the folder containing the VM files for easier identification.

### 3. Transfer Files to VirtualBox Directory
- Move the extracted folder to where your virtual machines are stored.

### 4. Set Up Kali Linux in VirtualBox
- Open VirtualBox.
- Use the `Machine` > `Add` option in the menu to browse and select the `.vbox` file from the pasted files.
- Click on `Settings` > `Network`
- Update Adapter1 to `Internal Network` and `cyber-range-lan`
- Make sure the pfSense vm is running and boot the Kali VM
- Default login for Kali is `kali kali`
- You can verify it got its ip address from pfSense by opening a shell and running `ip a`



## Conclusion
You have now successfully imported Kali Linux into your VirtualBox environment.

