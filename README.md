# Educational Network Infrastructure Deployment: A Windows Server 2019 and Windows 10 Integration Project

## Introduction
This project outlines the creation and configuration of a school network topology using Windows Server 2019 for server roles and Windows 10 Enterprise for client testing. The setup includes a domain controller, DHCP server, and file server, aimed at managing domain operations, dynamic IP allocation, and centralized resource sharing within a school environment.

## Objectives
- **Deploy a secure domain** for efficient network management.
- **Configure a DHCP server** for dynamic IP address allocation.
- **Set up a file server** for centralized educational resources access.
- **Incorporate a Windows 10 Enterprise client machine** to test the functionality of user accounts and access permissions.
- **Implement Group Policy** for security and access control.

## Technologies Used
- Windows Server 2019 for Domain Controller, DHCP Server, and File Server.
- Windows 10 Enterprise for client testing.
- Hyper-V for virtualization.
- Active Directory for domain services.
- DHCP services for network IP management.
- File services for centralized storage.

## Project Setup and Configuration

### Domain Controller: Thor
- **Role**: Domain management and authentication.
- **IP/Network Settings**: 10.0.0.101/255.255.255.0, DNS 127.0.0.1.
- **Key Configurations**: Creation of the domain `acs.edcc.ctc.edu`, Domain Admin account setup.

### DHCP Server: Atlas
- **Role**: IP address management.
- **IP/Network Settings**: 10.0.0.102/255.255.255.0, Gateway 10.0.0.101.
- **Key Configurations**: DHCP range setup, gateway, and DNS configuration.

### File Server: Zeus
- **Role**: Centralized file storage.
- **IP/Network Settings**: 10.0.0.103/255.255.255.0, Gateway 10.0.0.101.
- **Key Configurations**: Share `profile$` establishment for Domain Users with Full Control permissions.

### Windows 10 Enterprise Client Machine
- **Purpose**: To test the user accounts created in the domain controller, ensuring proper domain join, user authentication, and access to shared resources.
- **Configuration**: Joined to the `acs.edcc.ctc.edu` domain, tested various user roles for access and restrictions.

## Group Policy Configurations
- Remote Desktop enabled for Domain Admins and Users on all servers and client machines.
- Firewall disabled across all systems for uninterrupted network communication.

## Challenges and Solutions
Encountered DHCP configuration issues leading to IP conflicts. Adjusted the DHCP allocation range and excluded static IPs to resolve.

## Conclusion
The project successfully established a fully functional school network topology, enhanced by the integration of a Windows 10 Enterprise client machine for real-world user account testing. This approach provided valuable insights into the network's operational efficiency and security posture.

## Future Enhancements
Future improvements will focus on advanced security features, additional network services like print servers, and exploring scalability options to support network growth.
