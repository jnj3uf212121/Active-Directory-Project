# Active Directory Homelab Setup Documentation

## Overview
This document provides a detailed guide for setting up an Active Directory (AD) homelab with Hyper-V, resembling the network topology provided. It includes the creation of a domain controller (DC), a client, and necessary network settings to facilitate communication and domain services within a private lab environment.

## Prerequisites
- A host machine with Windows 10 Pro, Enterprise, or Education, or Windows Server with Hyper-V enabled.
- The host machine must have sufficient resources (CPU, RAM, and storage).
- Installation media for Windows Server and Windows 10 as ISO files.
- Basic understanding of Hyper-V, networking, and Windows Server administration.

## Hyper-V Configuration

### Virtual Switch Setup
1. **External Switch**: This switch provides VMs with internet access.
    - Open Hyper-V Manager.
    - Select 'Virtual Switch Manager' from the right pane.
    - Create a new virtual switch named "External" with the connection type set to 'External network'. Choose the host's network adapter that has internet access.
  
2. **Internal Switch**: This switch is used for internal lab communication.
    - Follow the steps above but select 'Internal' for the connection type.
    - Name this switch "Internal".

## Virtual Machine Creation

### Domain Controller (Server VM) Setup
1. In Hyper-V Manager, select 'New' -> 'Virtual Machine'.
2. Name the VM 'DC' and assign it at least 2 GB of RAM and 60 GB of Hard Disk space.
3. Attach the Windows Server ISO to the VM and install Windows Server.
4. Add two network adapters to the VM, connecting one to the External switch and the other to the Internal switch.
5. For the internal NIC, configure the following static IP settings:
   - IP address: `172.16.0.1`
   - Subnet mask: `255.255.255.0`
   - Default gateway: (Leave this field blank)
   - DNS: `127.0.0.1`

### Active Directory and DNS Configuration
1. Install the Active Directory Domain Services (AD DS) role using Server Manager.
2. Promote the server to a domain controller for a new forest with the Fully Qualified Domain Name (FQDN) `mydomain.com`.
3. Configure DNS to resolve for `mydomain.com`.
4. Optionally, install the DHCP role to manage IP distribution on the Internal network.

### Routing and Remote Access Setup (Optional)
- Configure the Routing and Remote Access Service (RRAS) on the DC to provide NAT for the Internal network, allowing VMs to share the DC's external IP for internet access.

### Windows Client VM Setup
1. Create another VM named 'Client1' with at least 2 GB of RAM and 40 GB of Hard Disk space.
2. Install Windows 10 and attach the VM to the Internal switch.
3. Configure the network settings to obtain an IP address automatically via DHCP (assumed to be set up on the DC).

## Domain Joining
- On the Windows 10 client VM, access 'System Properties' and join the machine to the `mydomain.com` domain using the credentials of a domain admin.

## Validation
- Verify that the client VM can log in using domain credentials.
- Ensure the client VM can access the internet if RRAS is configured correctly.

## Backup and Snapshot
- Regularly backup VM configurations and take snapshots before major changes.

## Troubleshooting
- Ensure Hyper-V services are running.
- Confirm network configurations are correctly applied.
- Verify the DC VM is running when attempting to join the domain or log in from the client VM.

## Conclusion
This homelab environment simulates a real-world network, allowing experimentation and learning with Active Directory, domain joining, and Windows Server features.

