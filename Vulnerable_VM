# Virtual Machine Setup Guide

This guide provides detailed instructions on how to download and set up two popular virtual machines (VMs), Metasploitable 2 and Mr. Robot, for penetration testing purposes. The process involves downloading VMs from Vulnhub, importing them, and configuring network settings. This document assumes the use of VirtualBox for VM management.

## Metasploitable 2 Setup

### Downloading and Importing the VM

1. **Download Metasploitable 2:**
   - Navigate to [Vulnhub](https://vulnhub.com).
   - Search for "Metasploitable".
   - Use the official Vulnhub mirror to download the VM archive.

2. **Extract the Virtual Disk:**
   - After downloading, unzip the file to extract the `.vmdk` virtual disk file, which is crucial for the next steps.

### Setting Up in VirtualBox

1. **Create a New VM:**
   - Open VirtualBox.
   - Click on the "New" button to start the VM creation wizard.

2. **Add the Downloaded Disk:**
   - Click on the "Add disk" icon.
   - Navigate to the folder where you unzipped Metasploitable2.
   - Open the folder, select the `.vmdk` file, and choose "Select".
   - Click "Next" and follow through the wizard until you can click "Finish".

### Important Note

- **Do Not Start the VM Yet:**
  - Right-click the newly created Metasploitable2 VM in VirtualBox and choose "Settings".
  - Navigate to the "Network" settings to ensure everything is configured correctly before starting the VM.

### First Boot and Network Configuration

1. **Start the VM:**
   - Once the network settings are configured, you can start the VM.

2. **Login Credentials:**
   - Use the default login credentials (`msfadmin:msfadmin`) to access the VM.
   - Verify that the system has obtained an IP address from the DHCP server (e.g., `10.6.6.11`).

### Connectivity Tests

1. **Ping Tests:**
   - Perform ping tests from Metasploitable2 to Kali Linux using the IP address and local DNS suffix.
   - Try pinging `google.com` from Metasploitable2 to confirm external connectivity is blocked as expected.
   - From Kali Linux, ping Metasploitable2 to ensure network connectivity is established.

### Final Steps

- **Snapshot:**
  - After verifying the VM's functionality, power it off and take a snapshot. This allows you to revert to a known good state if needed during your penetration testing activities.

## Mr. Robot VM Setup

### Downloading and Importing the VM

1. **VM Information and Download:**
   - VM details can be found on Vulnhub: [Mr. Robot](https://www.vulnhub.com/entry/mr-robot-1,151/).
   - Download the VM from the provided [link](https://download.vulnhub.com/mrrobot/mrRobot.ova).

### .OVA File Explanation

- The `.ova` file is an Open Virtual Appliance format, an open standard for packaging and distributing virtual appliances or more complex virtual machines across different hypervisors. VirtualBox directly supports this format, making it easy to import.

### Import Process in VirtualBox

1. **Import the VM:**
   - Double-click the `mrRobot.ova` file to initiate the import process in VirtualBox.
   - Set the VM name to "Mr. Robot".
   - Adjust the MAC address policy as needed.
   - Click "Finish" to complete the import.

### VM Configuration

1. **Adjust Settings:**
   - Right-click the "Mr. Robot" VM in VirtualBox and select "Settings" to adjust any configurations, particularly network settings.

2. **Network Configuration:**
   - Add the VM to an isolated network to ensure secure testing environment.
   - Confirm the VM obtains an IP address from pfSense in the Isolated LAN, assuming your firewall is configured correctly to allow routing from Kali to this LAN.

### Final Steps

- **Snapshot:**
  - Similar to Metasploitable2, once Mr. Robot VM is successfully booted and network configuration is verified, power it off and take a snapshot. This precaution ensures you can easily revert to a stable state if any issues arise during penetration testing.


