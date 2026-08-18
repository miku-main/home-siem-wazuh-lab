# home-siem-wazuh-lab

## Project Overview

This project documents my process of building a home SOC lab using Wazuh as the SIEM.

The goal of this lab is to gain hands-on experience with:

- SIEM deployment
- Endpoint monitoring
- Log analysis
- Threat detection
- File integrity monitoring
- Vulnerability detection
- Incident investigation
- SOC analyst workflows

## Lab Environment

### Wazuh Server

- Wazuh Version: 4.14.7
- Deployment Method: Wazuh OVA
- Hypervisor: VMware Workstation Pro
- Memory: 8 GB
- CPU: 4 cores
- Storage: 50 GB

## Installation Progress

### 1. VMware Workstation Setup

I installed VMware Workstation Pro on my Windows system to create and manage the virtual machines used in this lab.

Virtualization initially failed because AMD-V was disabled in the BIOS.

To resolve this, I entered the MSI BIOS and enabled:

`SVM Mode`

After enabling SVM Mode, I get a pop up that the CPU has been disabled by the guest operating system.

If you didn't get any pop up then ignore doing this part.

To fix this, you go to File Explorer and go to the path C:\Users\Name\Documents\Virtual Machines\Wazuh-SIEM, right click on Wazuh-SIEM and make sure the file type is VMware virtual machine configuration (.vmc).

Open it on notepad and paste this at the very bottom.
```bash
checkpoint.vmState = ""
cpuid.0.eax = "0000:0000:0000:0000:0000:0000:0000:1011"
cpuid.0.ebx = "0111:0101:0110:1110:0110:0101:0100:0111"
cpuid.0.ecx = "0110:1100:0110:0101:0111:0100:0110:1110"
cpuid.0.edx = "0100:1001:0110:0101:0110:1110:0110:1001"
cpuid.1.eax = "0000:0000:0000:0001:0000:0110:0111:0001"
cpuid.1.ebx = "0000:0010:0000:0001:0000:1000:0000:0000"
cpuid.1.ecx = "1000:0010:1001:1000:0010:0010:0000:0011"
cpuid.1.edx = "0000:0111:1000:1011:1111:1011:1111:1111"
featureCompat.enable = "FALSE"
```
Afterward I was able to successfully start virtual machines.

### 2. Wazuh OVA Deployment

I downloaded the official Wazuh 4.14.7 OVA and imported it into VMware Workstation.

The Wazuh virtual machine was configured with:

- 8 GB RAM
- 4 CPU cores
- 50 GB Virtual Disk
- Bridged network adapter

After starting the VM, I logged into the Wazuh server and identified its local IP address using:

```bash
ip addr
```

### 3. Wazuh Dashboard Access

I accessed the Wazuh Dashboard through my browser using the server's local IP address:
https://<WAZUH-SERVER-IP>

The dashboard successfully loaded and confirmed that the Wazuh server was operational.

Currently no endpoint agents have been deployed yet.

I have learned how virtualization is required to run the Wazuh lab environment and how the Wazuh OVA simplifies the deployment of the SIEM server. I also learned that the Wazuh server provides the central location where endpoint data and security alerts will eventually be collected and analyzed.
