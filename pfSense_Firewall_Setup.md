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

   ![WebPortal1](https://github.com/mjohansona2/Home-Lab/assets/6199686/40901332-69b5-4230-828a-015b913c27b3)

2. **Advanced Option**: Click `Advanced`.

3. **Login Credentials**: Use the default credentials to log in.
   - Username: `admin`
   - Password: `pfsense`

   ![WebPortal4](https://github.com/mjohansona2/Home-Lab/assets/6199686/4de08825-f0d7-471e-b4b5-f616a66c02b0)

4. **Initial Setup**: Click `Next` through the initial setup screens, filling out the `Hostname`, `Domain`, and adjusting settings such as DNS, timezone, and WAN network configuration as guided.

   ![WebPortal5](https://github.com/mjohansona2/Home-Lab/assets/6199686/fa39b5bd-3051-40b2-adea-e80868285686)
   ![WebPortal6](https://github.com/mjohansona2/Home-Lab/assets/6199686/7466111f-945a-41f2-815f-bb17a7012028)
   ![WebPortal7](https://github.com/mjohansona2/Home-Lab/assets/6199686/b1436dff-aa02-4998-ac37-c8d9e77a509d)
   ![WebPortal8](https://github.com/mjohansona2/Home-Lab/assets/6199686/fb702413-a0b6-4d10-8e09-53b96cffbf95)

## Configuring the Interfaces

### Isolated Interface

1. **Choose Interface**: Navigate to `Interfaces`, select `OPT1`.

   ![WebPortal9](https://github.com/mjohansona2/Home-Lab/assets/6199686/74821458-6de2-4b49-a22b-56f650f4381b)

2. **Set Description**: Enter `Isolated` as the description.

   ![WebPortal10](https://github.com/mjohansona2/Home-Lab/assets/6199686/8266bb15-af7a-4b4f-a783-30ac1ba193bc)

3. **Apply Changes**: Click `Save` and then `Apply Changes`.

### AD_LAB Interface

1. **Select Interface**: Go to `Interfaces`, choose `OPT2`.
2. **Description**: Set the description to `AD_LAB`.
3. **Save Settings**: Click `Save` and `Apply Changes`.

   ![WebPortal11](https://github.com/mjohansona2/Home-Lab/assets/6199686/06208ee6-897f-4403-b2a3-c58b1fac504d)

## Optimizing the DNS Resolver Service

1. **DNS Resolver Settings**: Navigate to `Services > DNS Resolver`.

   ![WebPortal12](https://github.com/mjohansona2/Home-Lab/assets/6199686/48b28f68-2e34-4d84-b60e-5695a98babf5)

2. **Adjustments**: Check the required boxes for optimization.

   ![WebPortal13](https://github.com/mjohansona2/Home-Lab/assets/6199686/9bf0845a-0a2d-407e-922b-87d08d336f1e)
   ![WebPortal14](https://github.com/mjohansona2/Home-Lab/assets/6199686/4aa3c659-eb0e-4cb0-956c-329e76bf1a4c)

3. **Apply Changes**: Click `Save` and `Apply Changes`.

## Assigning a Static DHCP Lease to Kali

1. **DHCP Leases**: Go to `Status > DHCP Leases`.

   ![WebPortal16](https://github.com/mjohansona2/Home-Lab/assets/6199686/620d4ca0-8479-44cd-9ac9-dfcd7338cb52)

2. **Static Mapping**: Add a static mapping for Kali with IP `10.0.0.2`.

   ![WebPortal17](https://github.com/mjohansona2/Home-Lab/assets/6199686/c50a27b4-06bb-409c-a866-cd82fd7a3a3c)
   ![WebPortal18](https://github.com/mjohansona2/Home-Lab/assets/6199686/82290c94-d602-4fc8-89bf-459e9b492885)

## Configuring Firewall Rules

### Creating Aliases

   ![WebPortal19](https://github.com/mjohansona2/Home-Lab/assets/6199686/eb730c9d-8f45-4ef9-82ef-7f1a0e418e6a)

- **RFC1918 Alias**: This alias represents all private IPv4 spaces. Navigate to `Firewall > Aliases` to add it.

   ![WebPortal20](https://github.com/mjohansona2/Home-Lab/assets/6199686/6b6676cf-9068-4f69-8681-cc75a900aaae)

- **Kali Alias**: Similarly, add an alias for the Kali VM for easy reference in rules.

  ![WebPortal21](https://github.com/mjohansona2/Home-Lab/assets/6199686/343b9d76-32fe-47d9-b0e8-7babb87f2099)

### Setting Up LAN Rules

1. **LAN Rules**: Block unwanted access while allowing necessary traffic.

   ![WebPortal22](https://github.com/mjohansona2/Home-Lab/assets/6199686/c3c8ec16-159b-492f-a87d-f3932416975f)

2. **Configuration**: Define rules to block and pass traffic based on the network's needs.

   ![WebPortal23](https://github.com/mjohansona2/Home-Lab/assets/6199686/66d66f66-dd49-444d-96f4-ad60366b65a7)
   ![WebPortal24](https://github.com/mjohansona2/Home-Lab/assets/6199686/96c4d364-3b37-4bac-9f57-edd982290703)

### Configuring ISOLATED and AD_LAB Rules

- **Rules Overview**: Set up rules for `ISOLATED` and `AD_LAB` interfaces to manage traffic flow, including allowing traffic to Kali and blocking all else as needed.

- **Click ISOLATED and Add**: 
   ![WebPortal25](https://github.com/mjohansona2/Home-Lab/assets/6199686/268ff7db-32d2-4e1a-aedf-2552c8a61a15)

- **Click AD_LAB and click add**:

   ![WebPortal26](https://github.com/mjohansona2/Home-Lab/assets/6199686/2508015f-9aeb-4bda-a280-d157b122f141)

- **Click Add Again for AD_LAB**:

   ![WebPortal27](https://github.com/mjohansona2/Home-Lab/assets/6199686/0ff4765d-f15b-4a50-a5a4-aadb86e8fbfd)

- ***Click Add Again for AD_LAB**:

   ![WebPortal28](https://github.com/mjohansona2/Home-Lab/assets/6199686/e8c6253c-10fd-49af-a5f6-516849f3a3ae)
  
## Making System Tweaks to pfSense

1. **System Adjustments**: Navigate to `System > Advanced > Networking`.

   ![WebPortal29](https://github.com/mjohansona2/Home-Lab/assets/6199686/ed8f4a77-5f61-4e6c-aa0f-d67ce9b7fa6e)
   ![WebPortal30](https://github.com/mjohansona2/Home-Lab/assets/6199686/68310d6c-78bb-4794-a656-e76cf3067c5b)

2. **Apply Changes**: Check necessary boxes and apply changes. Reboot pfSense.

## Verifying
- **After pfSense restarts, restart the network in Kali to grab the assigned IP**:
- **Before**:

   ![WebPortal31](https://github.com/mjohansona2/Home-Lab/assets/6199686/b8bbdffe-2c8b-41eb-94e1-1a41b932ce28)

- **Restarting networking**:

   ![WebPortal32](https://github.com/mjohansona2/Home-Lab/assets/6199686/bb4dee87-a4cb-46d8-9bc1-e92fbfdb329d)

- **After**:

   ![WebPortal33](https://github.com/mjohansona2/Home-Lab/assets/6199686/9e7641ee-5fc5-4527-9b23-416b6fed6aa5)
