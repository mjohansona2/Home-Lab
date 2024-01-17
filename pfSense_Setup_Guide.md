
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

**Important**: Do not start the VM yet!

## Step 3: Customize VM Settings
1. Right-click the VM and select **Settings**.
2. Adjust the boot order: Move **Hard Disk** above **Optical** and disable **Floppy**.
3. Disable audio and USB features.

## Step 4: Configure Network Interfaces
Configure each of the following adapters with paravirtualized drivers for optimal performance:
1. Adapter 1: WAN
2. Adapter 2: LAN
3. Adapter 3: ISOLATED
4. Adapter 4: AD_LAB

Click **OK** when done.

## Step 5: Install pfSense
1. Start the VM and select the `.iso` file downloaded earlier.
2. Choose **Install pfSense** and then **Auto (ZFS)**.
3. Proceed with the default installation settings, selecting Stripe – No Redundancy.
4. Use the Space Bar to select the disk and arrow keys to confirm selections.
5. After installation, select **Reboot**.

## Step 6: Configuring pfSense
1. Upon reboot, when prompted to set up VLANs, select `n`.
2. Specify interfaces for WAN, LAN, ISOLATED, and AD_LAB as prompted.

## Step 7: Configure Network Interfaces
**LAN Configuration**:
1. Select option 2 for LAN.
2. Set a static IP address and subnet mask.
3. Skip IPv6 settings.
4. Enable DHCP server and set IP range.
5. Choose `n` for TLS configuration.

**Isolated LAN Configuration**:
Repeat the LAN configuration steps for the Isolated LAN (OPT3).

**AD_LAB LAN Configuration**:
1. Configure OPT4 similarly, but disable the DHCP server as the domain controller will handle this role.

## Step 8: Final Check
Verify the configuration settings in the VM.

## Security Note
Do not make the pfSense web console accessible from the WAN for security reasons. Use a secure VM like Kali for firewall rule configuration.

## Next Step
Proceed to import Kali from Offensive Security Images.
