
# Setting Up pfSense Firewall VM in VirtualBox for Home Lab Network

**Note**: pfSense acts as the NAT router and firewall in your lab environment. It must be the first VM to boot in your lab setup.

## Step 1: Download pfSense
1. Visit [pfSense Download Page](https://www.pfsense.org/download/).
2. Select the following options:
   - Architecture: AMD64
   - Installer: ISO
   - Mirror: Choose nearest to your location
3. After downloading, use `7zip` or another extraction tool to decompress the `.gz` archive, resulting in a file named `pfSense-CE-#.#.#-RELEASE-amd64.iso`.

## Step 2: Create the VM in VirtualBox
1. Open VirtualBox and click the **New** button.
2. Fill in **Name** and **Machine Folder** according to your preference.
3. Ensure you select the correct **Type** and **Version** as specified.
![pfsense1](https://github.com/mjohansona2/Home-Lab/assets/6199686/7b734ade-b72c-4d6f-9056-b1a2a1cd301f)

**Important**: Do not start the VM yet!

## Step 3: Customize VM Settings
1. Right-click the VM and select **Settings**.
2. Adjust the boot order: Move **Hard Disk** above **Optical** and disable **Floppy**.

![pfsense4](https://github.com/mjohansona2/Home-Lab/assets/6199686/62333ffb-991d-4b4e-8663-a4f1eb28f773)

3. Disable audio and USB features.

![pfsense5](https://github.com/mjohansona2/Home-Lab/assets/6199686/f19bfba9-1f8b-436b-8672-27687974d144) ![pfsense6](https://github.com/mjohansona2/Home-Lab/assets/6199686/e3c1adc6-8b8e-4c04-88f8-12f73db0aef8)


## Step 4: Configure Network Interfaces
Configure each of the following adapters with paravirtualized drivers for optimal performance:
1. Adapter 1: WAN

![pfsense-network1](https://github.com/mjohansona2/Home-Lab/assets/6199686/b8f94894-e18e-400c-8161-19fd38482d42)

3. Adapter 2: LAN

![pfsense-network2](https://github.com/mjohansona2/Home-Lab/assets/6199686/51f64483-c461-4b24-b474-549ef4b50ff6)

4. Adapter 3: ISOLATED

![pfsense-network3](https://github.com/mjohansona2/Home-Lab/assets/6199686/fe6cf908-98b9-4b96-bb46-b0dc5ed0eb2c)

5. Adapter 4: AD_LAB

![pfsense-network4](https://github.com/mjohansona2/Home-Lab/assets/6199686/84960fdc-cbcb-4c87-8b22-537c989cf4d5)

Click **OK** when done.

## Step 5: Install pfSense
1. Start the VM and select the `.iso` file downloaded earlier.
2. Choose **Install pfSense** and then **Auto (ZFS)**.

![pfsense-install2](https://github.com/mjohansona2/Home-Lab/assets/6199686/428d1a64-4465-45a8-aceb-977ddef91725)
![pfsense-install3](https://github.com/mjohansona2/Home-Lab/assets/6199686/219d94ba-2d24-4108-8c60-6ef839837dbb)

3. Proceed with the default installation settings, selecting Stripe – No Redundancy.

![pfsense-install5](https://github.com/mjohansona2/Home-Lab/assets/6199686/5636f52f-6274-4acf-98a0-28694c695be8)


4. Use the Space Bar to select the disk and arrow keys to confirm selections.

![pfsense-install6](https://github.com/mjohansona2/Home-Lab/assets/6199686/8265ea8f-eff3-482b-a718-86637b0c2352)

5. After installation, select **Reboot**.

![pfsense-install9](https://github.com/mjohansona2/Home-Lab/assets/6199686/6d10a215-d754-497b-bb06-32b0ae110138)

## Step 6: Configuring pfSense
1. Upon reboot, when prompted to set up VLANs, select `n`.

![pfsense-install10](https://github.com/mjohansona2/Home-Lab/assets/6199686/ffb900a1-7df0-497b-b0d0-587355be62e9)

2. Specify interfaces for WAN, LAN, ISOLATED, and AD_LAB as prompted.

![pfsense-install11](https://github.com/mjohansona2/Home-Lab/assets/6199686/7ff20490-98ff-4522-bc12-7fa4e6a87d70)

## Step 7: Configure Network Interfaces
**LAN Configuration**:
1. Select option 2 for Setting INterfaces IP addresses

![pfsense-install16](https://github.com/mjohansona2/Home-Lab/assets/6199686/07d9d581-37ba-4653-92df-73e9c8f1c386)

2. Select 2 for the LAN:

![pfsense-install17](https://github.com/mjohansona2/Home-Lab/assets/6199686/2ac37c61-842c-489d-941a-7d400254f9c7)

3. Set a static IP address and subnet mask.

![pfsense-install18](https://github.com/mjohansona2/Home-Lab/assets/6199686/a000a23c-b5e6-4b03-b11e-38afe34f6e04)
![pfsense-install19](https://github.com/mjohansona2/Home-Lab/assets/6199686/46504b25-8e0d-4e76-91cb-1a4009736808)
![pfsense-install20](https://github.com/mjohansona2/Home-Lab/assets/6199686/e834f614-d19b-4c6e-8a5d-6868791a44f6)

4. Press Enter for LAN:

![pfsense-install21](https://github.com/mjohansona2/Home-Lab/assets/6199686/0fc5f2c2-4dc6-4459-baff-91a3ccad403f)

5. Skip IPv6 settings.

![pfsense-install22](https://github.com/mjohansona2/Home-Lab/assets/6199686/77da1cba-6137-4abe-8c34-ebf4bebbd025)
![pfsense-install23](https://github.com/mjohansona2/Home-Lab/assets/6199686/853435ea-82a3-45b9-9277-7fa0dce62284)

6. Enable DHCP server and set IP range.

![pfsense-install24](https://github.com/mjohansona2/Home-Lab/assets/6199686/cf4364a0-85b3-4138-8516-29db84ffd2f2)

7. Choose `n` for web configuration.

![pfsense-install25](https://github.com/mjohansona2/Home-Lab/assets/6199686/cae88281-5c46-4091-80ca-f0b16a9df74b)


**Isolated LAN Configuration**:
Repeat the LAN configuration steps for the Isolated LAN (OPT1).

![pfsense-install28](https://github.com/mjohansona2/Home-Lab/assets/6199686/8c012da4-883f-45c1-9d4e-c12b758811e2)
![pfsense-install29](https://github.com/mjohansona2/Home-Lab/assets/6199686/9ad48893-40ec-4204-864d-ff25db6c3bd3)
![pfsense-install30](https://github.com/mjohansona2/Home-Lab/assets/6199686/af764959-90d8-48c0-8ffb-86c6cae276b0)



**AD_LAB LAN Configuration**:
Configure OPT2 similarly, but disable the DHCP server as the domain controller will handle this role.

![pfsense-install24](https://github.com/mjohansona2/Home-Lab/assets/6199686/ebef864e-c87f-4303-b7dd-aee6a40478a1)
![pfsense-install32](https://github.com/mjohansona2/Home-Lab/assets/6199686/68cec41d-31f6-45b7-8156-1d0ae6bf8154)

## Step 8: Final Check
Verify the configuration settings in the VM.

![pfsense-install34](https://github.com/mjohansona2/Home-Lab/assets/6199686/1002b12c-c10e-4aaa-96f1-5e9815be1d4d)


## Next Step
Proceed to import Kali from Offensive Security Images.
