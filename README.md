# Lab Report: Setting Up a Windows Server 2022 for Active Directory Penetration Testing
### Objective:
The aim of this lab is to set up a Windows Server 2022 in a virtual environment for the purpose of learning and testing Active Directory penetration techniques. This is part of the “Build it & Break it” series, which focuses on understanding and attacking specific technologies.

### Materials:

- Virtualization Software (Oracle Virtual Box, VMware Player, or VMware Workstation Pro)
- Windows Server 2022 ISO (available from Microsoft Evaluation Center)
- A computer capable of running virtualization software

## Procedure:

## Creating a New Virtual Machine:

### 1. Launch VMware Workstation Pro.
- Select “File” > “New Virtual Machine.”
- Choose the “Typical (Recommended)” setup option.

### 2. Configuring the Virtual Machine:
- Choose “Installer disc image file (iso)” and select the downloaded Windows Server 2022 ISO.
- Set the “Guest Operating System” as Windows.

### Customizing Hardware Specifications:
- Allocate 2 virtual processors.
- Assign 2 GB of RAM.

### Setting up Network Adapters:
- Adapter #1: Set as NAT for internet connection.
- Adapter #2: Configure as VMNet0 for private lab network.

### Installing Windows Server 2022:
- Power on the virtual machine and boot from the ISO file.
- Follow the installation wizard: click “Next,” then “Install Now.”

### Selecting Installation Type:
- Choose “Standard Evaluation (Desktop Experience)” for a full graphical experience.

### Disk Partitioning and OS Installation:
- Agree to Microsoft Software License Terms.
- Select “Custom” install and choose “Drive0 Unallocated Space” for installation.

### Completing the Installation:
- Wait for the installation to complete and the server to reboot.
- Configure the local Administrator password.

### Configuring Display Settings:
- Adjust display resolution to fit the screen from the “Settings” menu.

### Configuring Network Adapters:
- Rename the adapters for clarity: one as External (NAT) and the other as Internal.
- Leave the NAT network untouched.
- Assign the Internal adapter an IP of 10.10.10.5 with a subnet mask of 255.255.255.0.

### Setting Up Internal Network:
- Configure the server with an IP of 10.10.10.5 in the 10.10.10.0/24 range.
- Set DNS to either 10.10.10.5 or a loopback of 127.0.0.1.

### Verifying Network Configuration:
- Check the assigned IP in the “Server Manager” dashboard.

### Adjusting Time Zone:
- Optionally, change the server’s time zone to match the local time zone.

### Renaming the Server:
- Rename the server to a meaningful name, e.g., “DC01.”
- Restart the server to apply changes.

### Creating a VM Snapshot:
- Take a Snapshot of the VM state post-setup for backup purposes.

## Results and Discussion:
The setup of Windows Server 2022 was successful, with all necessary configurations for a lab environment aimed at Active Directory penetration testing. The virtual machine was configured with appropriate hardware resources, network settings were established for both external and internal communications, and the operating system was installed and configured correctly. The use of snapshots ensures a restore point for future experiments.

## Conclusion:
The lab setup is now ready for further steps in learning about Active Directory and conducting penetration testing. The environment provides a controlled space for experimenting with various attacks against Active Directory, essential for understanding the security aspects of Windows infrastructure. Future posts in the series will delve deeper into Active Directory configurations and attack methodologies.
