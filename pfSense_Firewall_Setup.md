# pfSense Configuration Guide

This guide provides step-by-step instructions on how to configure pfSense, including setting up interfaces, optimizing the DNS Resolver service, and configuring firewall rules. This document is designed for use with a Kali Linux VM as a part of the setup process.

## Table of Contents

- [Logging into pfSense Web Portal](#logging-into-pfsense-web-portal)
- [Configuring the Interfaces](#configuring-the-interfaces)
  - [Isolated Interface](#isolated-interface)
  - [AD_LAB Interface](#ad_lab-interface)
- [Optimizing the DNS Resolver Service](#optimizing-the-dns-resolver-service)
- [Assigning a Static DHCP Lease to Kali](#assigning-a-static-dhcp-lease-to-kali)
- [Configuring Firewall Rules](#configuring-firewall-rules)
  - [Creating Aliases](#creating-aliases)
  - [Setting Up LAN Rules](#setting-up-lan-rules)
  - [Configuring ISOLATED and AD_LAB Rules](#configuring-isolated-and-ad_lab-rules)
- [Making System Tweaks to pfSense](#making-system-tweaks-to-pfsense)
- [Verifying Kali's DHCP Reservation](#verifying-kalis-dhcp-reservation)

## Logging into pfSense Web Portal

1. **Access the Portal**: On Kali, open your web browser and navigate to `https://10.0.0.1`.

   ![Login Screen](images/login-screen.png)

2. **Advanced Option**: Click `Advanced`.

3. **Login Credentials**: Use the default credentials to log in.
   - Username: `admin`
   - Password: `pfsense`

   ![Credentials](images/credentials.png)

4. **Initial Setup**: Click `Next` through the initial setup screens, filling out the `Hostname`, `Domain`, and adjusting settings such as DNS, timezone, and WAN network configuration as guided.

   ![Setup Steps](images/setup-steps.png)

## Configuring the Interfaces

### Isolated Interface

1. **Choose Interface**: Navigate to `Interfaces`, select `OPT1`.
2. **Set Description**: Enter `Isolated` as the description.
3. **Apply Changes**: Click `Save` and then `Apply Changes`.

   ![Isolated Interface](images/isolated-interface.png)

### AD_LAB Interface

1. **Select Interface**: Go to `Interfaces`, choose `OPT2`.
2. **Description**: Set the description to `AD_LAB`.
3. **Save Settings**: Click `Save` and `Apply Changes`.

   ![AD_LAB Interface](images/ad_lab-interface.png)

## Optimizing the DNS Resolver Service

1. **DNS Resolver Settings**: Navigate to `Services > DNS Resolver`.
2. **Adjustments**: Check the required boxes for optimization.
3. **Apply Changes**: Click `Save` and `Apply Changes`.

   ![DNS Resolver](images/dns-resolver.png)

   **Note**: As of Jan 1, 2024, Netgate suggests moving to the Kea DHCP daemon. Adjustments to the DNS resolver related to DHCP registration require toggling between ISC and Kea if needed.

## Assigning a Static DHCP Lease to Kali

1. **DHCP Leases**: Go to `Status > DHCP Leases`.
2. **Static Mapping**: Add a static mapping for Kali with IP `10.0.0.2`.

   ![Static DHCP Lease](images/static-dhcp.png)

## Configuring Firewall Rules

### Creating Aliases

- **RFC1918 Alias**: This alias represents all private IPv4 spaces. Navigate to `Firewall > Aliases` to add it.
- **Kali Alias**: Similarly, add an alias for the Kali VM for easy reference in rules.

  ![Creating Aliases](images/creating-aliases.png)

### Setting Up LAN Rules

1. **LAN Rules**: Block unwanted access while allowing necessary traffic.
2. **Configuration**: Define rules to block or pass traffic based on the network's needs.

   ![LAN Rules](images/lan-rules.png)

### Configuring ISOLATED and AD_LAB Rules

- **Rules Overview**: Set up rules for `ISOLATED` and `AD_LAB` interfaces to manage traffic flow, including allowing traffic to Kali and blocking all else as needed.

  ![ISOLATED and AD_LAB Rules](images/interface-rules.png)

## Making System Tweaks to pfSense

1. **System Adjustments**: Navigate to `System > Advanced > Networking`.
2. **Apply Changes**: Check necessary boxes and apply changes. Consider rebooting pfSense if required.

   ![System Tweaks](images/system-tweaks.png)

## Verifying

