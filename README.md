# Vlan-configuration-
Cisco Packet Tracer lab practising VLAN creation, switch port assignment and network segmentation using a Cisco 2960 switch. Configured VLAN 5 and VLAN 20, assigned devices to access ports, and verified the VLAN configuration and connectivity

# VLAN Configuration Lab (VLAN Creation, Port Assignment and Network Segmentation)

`Cisco Packet Tracer` · `Cisco 2960 Switch` · `VLANs` · `Access Ports` · `Network Segmentation`

## Overview

This lab was hands-on practice with VLAN creation and switch port assignment using Cisco Packet Tracer. The goal was to create separate VLANs and assign different devices to the correct VLAN based on their switch ports.

The topology used a Cisco 2960 switch connected to a server and multiple PCs. VLAN 5 was used for PC1 and PC2, while VLAN 20 was assigned to PC0. The server remained in the default VLAN 1.

This helped me understand how VLANs can separate devices into different logical networks even when they are connected to the same physical switch.

## Objective

- Create VLAN 5 and VLAN 20
- Assign switch ports to the correct VLAN
- Keep the server in the default VLAN 1
- Understand how access ports connect devices to specific VLANs
- Verify the network configuration using connectivity testing

## Environment

- Lab platform: Cisco Packet Tracer
- Switch: Cisco 2960
- Devices: Server, PC1, PC2, PC0 and Admin Laptop
- VLAN 1: Default VLAN
- VLAN 5: PC1 and PC2
- VLAN 20: PC0

## Network Layout

| Device | Switch Port | VLAN |
|---|---|---:|
| Server0 | Fa0/1 | VLAN 1 |
| PC1 | Fa0/5 | VLAN 5 |
| PC2 | Fa0/15 | VLAN 5 |
| PC0 | Fa0/20 | VLAN 20 |
| Admin Laptop | Management connection | — |

The lab instructions showed the VLAN 1 address as:

`192.168.1.10`

## What I Did

### Creating the VLANs

I created the two required VLANs on the switch:

    enable
    configure terminal

    vlan 5
    name VLAN5
    exit

    vlan 20
    name VLAN20
    exit

This created separate logical networks for the devices that needed to be grouped together.

### Assigning PC1 to VLAN 5

PC1 was connected to FastEthernet 0/5, so I configured the port as an access port belonging to VLAN 5:

    interface fa0/5
    switchport mode access
    switchport access vlan 5
    exit

### Assigning PC2 to VLAN 5

PC2 was connected to FastEthernet 0/15:

    interface fa0/15
    switchport mode access
    switchport access vlan 5
    exit

Both PC1 and PC2 were therefore placed into the same VLAN.

### Assigning PC0 to VLAN 20

PC0 was connected to FastEthernet 0/20:

    interface fa0/20
    switchport mode access
    switchport access vlan 20
    exit

PC0 was therefore separated from the devices in VLAN 5.

### Server0 and VLAN 1

Server0 was connected to FastEthernet 0/1 and remained in the default VLAN 1 as instructed.

The lab diagram showed the VLAN 1 address as:

`192.168.1.10`

## Verifying the VLAN Configuration

After assigning the ports, the VLAN configuration can be checked with:

    show vlan brief

This allows you to confirm which ports belong to each VLAN.

The expected configuration was:

    VLAN 1  → Fa0/1
    VLAN 5  → Fa0/5, Fa0/15
    VLAN 20 → Fa0/20

Connectivity can then be tested using ping between appropriate devices.

## What I Learned

- VLANs separate devices logically even when they use the same physical switch.
- Access ports are normally assigned to a single VLAN.
- Devices connected to Fa0/5 and Fa0/15 were placed into VLAN 5.
- A device connected to Fa0/20 was placed into VLAN 20.
- The server remained in the default VLAN 1.
- `show vlan brief` is useful for checking VLAN and port assignments.
- VLANs can help improve network organisation, segmentation and security.

## VLAN Structure

    Cisco 2960 Switch
           |
    +------+-------+----------------+
    |              |                |
    VLAN 1       VLAN 5          VLAN 20
    |              |                |
    Server0     +--+--+             PC0
    Fa0/1       |     |            Fa0/20
               PC1   PC2
              Fa0/5 Fa0/15

## How This Applies in the Real World

VLANs are commonly used in business networks to separate different groups of devices.

For example, an organisation could use separate VLANs for:

- Employees
- Servers
- Guest devices
- Security cameras
- Voice/VoIP phones
- Management devices

This can reduce unnecessary network traffic and provide network segmentation, making it easier to control which devices can communicate with each other.

From a cybersecurity perspective, VLANs can also form part of a defence-in-depth strategy. However, simply putting devices into different VLANs does not automatically prevent communication between them; additional controls such as routing rules, ACLs or firewalls may be required.

## What's in This Repo

    vlan-configuration-lab/
    ├── README.md
    └── screenshots/
        └── vlan-topology.png

## Skills I Practiced

- Creating VLANs
- Assigning switch ports to VLANs
- Configuring access ports
- Understanding VLAN segmentation
- Working with Cisco 2960 switches
- Reading a network topology
- Using `show vlan brief` for verification
- Using ping for connectivity testing
- Understanding the difference between the default VLAN and configured VLANs

## What I Want to Learn Next

- Configuring trunk ports
- Understanding 802.1Q tagging
- Configuring inter-VLAN routing
- Using router-on-a-stick
- Configuring VLAN ACLs
- Troubleshooting VLAN connectivity with `show` commands
- Building a larger enterprise network with multiple VLANs

## Limitations

This was a basic VLAN configuration exercise. It focused mainly on creating VLANs and assigning access ports rather than building a complete enterprise network.

No inter-VLAN routing was configured in this exercise, so the lab does not demonstrate communication between VLAN 5, VLAN 20 and VLAN 1 through a router or Layer 3 switch.

## Where I'm Coming From

I'm building these Packet Tracer labs as part of my transition into cybersecurity. My background is in healthcare, so I'm using practical networking and security labs to build hands-on experience alongside my CompTIA Security+ studies.

This lab helped reinforce an important cybersecurity concept: network segmentation can be used to separate systems and control how different parts of a network communicate.

## References

- Cisco – VLAN Configuration Guide: https://www.cisco.com/c/en/us/td/docs/switches/lan/c9000/lyr2-fwd/vlan/vlan-configuration-guide/configure-vlan.html
- Cisco – Configuring VLANs and Static Access Ports: https://www.cisco.com/en/US/docs/switches/lan/catalyst3850/software/release/3se/consolidated_guide/b_consolidated_3850_3se_cg_chapter_010000111.html
- Cisco Packet Tracer – Used to build and configure the network topology and practise VLAN configuration.
