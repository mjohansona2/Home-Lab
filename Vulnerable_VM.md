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

   ![metasploit1](https://github.com/mjohansona2/Home-Lab/assets/6199686/578c934f-ea82-4339-a196-8e862cb3ca10)

2. **Add the Downloaded Disk:**
   - Click on the "Add disk" icon.

   ![metasploit3](https://github.com/mjohansona2/Home-Lab/assets/6199686/bd80a95e-2344-4297-b7e5-6ca30bb2e963)

   - Navigate to the folder where you unzipped Metasploitable2.
   - Open the folder, select the `.vmdk` file, and choose "Select".

   ![metasploit4](https://github.com/mjohansona2/Home-Lab/assets/6199686/df226218-34c3-445c-8213-f1869a46fce9)

   - Click "Next" and follow through the wizard until you can click "Finish".

   ![metasploit5](https://github.com/mjohansona2/Home-Lab/assets/6199686/b68da0c5-40af-4c23-87de-85fc6029b738)


### Important Note

- **Do Not Start the VM Yet:**
  - Right-click the newly created Metasploitable2 VM in VirtualBox and choose "Settings".
  - Navigate to the "Network" settings to ensure everything is configured correctly before starting the VM.

   ![metasploit6](https://github.com/mjohansona2/Home-Lab/assets/6199686/af480189-24f2-4bb0-abf1-971db77bd2c3)

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

   ![metasploit8](https://github.com/mjohansona2/Home-Lab/assets/6199686/0150ee18-7e57-43cb-a279-43c54abe5f62)

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

   ![mrrobot1](https://github.com/mjohansona2/Home-Lab/assets/6199686/1391c515-09f2-41b8-9aa3-c8671c9d653d)

### VM Configuration

1. **Adjust Settings:**
   - Right-click the "Mr. Robot" VM in VirtualBox and select "Settings" to adjust any configurations, particularly network settings.

2. **Network Configuration:**
   - Add the VM to an isolated network to ensure secure testing environment.

   ![mrrobot2](https://github.com/mjohansona2/Home-Lab/assets/6199686/e9c42073-27d0-437c-a452-f063f65f5ee5)

   - Confirm the VM obtains an IP address from pfSense in the Isolated LAN, assuming your firewall is configured correctly to allow routing from Kali to this LAN.

### Final Steps

- **Snapshot:**
  - Similar to Metasploitable2, once Mr. Robot VM is successfully booted and network configuration is verified, power it off and take a snapshot. This precaution ensures you can easily revert to a stable state if any issues arise during penetration testing.
