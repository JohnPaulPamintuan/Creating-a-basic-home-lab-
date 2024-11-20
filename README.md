# Setting Up a Home Lab for Cybersecurity
## Project Overview
This project combines setting up a secure home lab environment for cybersecurity testing with generating and analyzing telemetry from simulated malicious activity. 
The goal is to experiment with offensive techniques and detect malicious behaviors using monitoring tools, such as Sysmon and Splunk. By combining VM configuration, malware creation, and telemetry analysis, this project offers a comprehensive learning experience.



## Table of Contents
1. Introduction
    - Goals
2. Setting up the Home Lab
    - Installation of VirtualBox
    - Creating Virtual Machines
3.  Network Configuration for Secure Testing
    - Network Options in VirtualBox
    - Step-by-Step Configuration Guide
    - VM Best Practices and Snapshots
4.  Generating Telemetry from Malicious Activity
    - Tools & Techniques Used
    - Skills demonstrated
    - Step-by-Step Guide
5. Conclusion


# 1. Introduction 
Establishing a home lab is an essential step in cybersecurity, allowing for the safe testing of tools, techniques, and simulations without affecting real-world systems. This project goes beyond setting up a basic lab, integrating offensive techniques such as malware execution and analyzing system telemetry to detect malicious activity. The project emphasizes the importance of understanding both attack and defense methods within a secure virtualized environment.

##  Goals
- <b>Learn by Doing </b>: Gain practical experience with cybersecurity tools and techniques.
- <b>Safe Experimentation</b>: Test exploits, analyze malware, and practice defense strategies without impacting live systems.
- <b>Skill Development</b>: Enhance skills in areas like penetration testing, digital forensics, and incident response.


# 2. Setting Up the Home Lab
To begin with, we'll create a virtualized environment using VirtualBox or VMware. This isolated environment enables safe testing of cybersecurity tools and malware, without risking your physical machine. For this project, we’ll use VirtualBox, a free and widely used tool for virtualization.

 ## Installing VirtualBox
- Download VirtualBox: Go to VirtualBox.org and download the appropriate version for your operating system.
- Verify the SHA-256 Hash: Ensure the downloaded file is legitimate by checking its hash against the official value.
- Complete the Installation: Follow the installation prompts and customize any settings as needed.

IMAGE
IMAGE
IMAGE 
## Creating Virtual Machines (VMs)
- Windows 10 VM:
  - Use the Media Creation Tool to create a Windows 10 ISO and set up a VM with at least 4GB RAM and 2 CPUs.
- Kali Linux VM:
  - Download a pre-built Kali Linux ISO from Kali.org and set up a VM for penetration testing tools.

IMAGE 
IMAGE 

# Network Configuration for Secure Testing
VirtualBox offers several network modes to control how your VMs communicate with each other and the host system. The correct configuration is essential for securing your testing environment, especially when working with potentially malicious software.

## Network Options in VirtualBox
- NAT: Default setting, gives the VM access to the internet but isolates it from the host network. Ideal for tool testing.
IMAGE

- NAT Network: Allows multiple VMs to share the same network while maintaining internet access.
IMAGE
- Bridged: The VM acts like a physical device on your local network. Not recommended for malware analysis as it increases the risk of compromising the host.
IMAGE
- Host-Only: Only allows communication between the host and VMs. No internet access.
IMAGE
- Internal Network: Isolates the VM network from the host and the internet. Best for malware analysis as VMs can communicate only with each other.
IMAGE
- Not Attached: No network connection. Ideal for maximum isolation.
- IMAGE

## Step-by-Step Configuration Guide for setting up your VMs and configuring network settings:
Create a new VM for Windows 10 or Kali Linux.
Assign sufficient resources (RAM, CPU, storage) based on your system’s capabilities.
Choose Network Settings:
For testing tools, select NAT.
For malware analysis, select Internal Network or Not Attached.
Configure static IP addresses for VM communication (e.g., use ipconfig in Windows and ifconfig in Kali).
Take a snapshot after configuring the VM to preserve the setup.
IMAGE
IMAGE
IMAGE

## VM Best Practices and Snapshots
To protect your home lab and ensure the stability of your VMs, follow these best practices:

- VM Configuration
  - Resource Allocation: Do not over-provision resources (e.g., CPU, RAM, storage) as it can slow down both the host and VMs.
  - Isolation: Always isolate malware testing VMs from the host using Internal Network or Not Attached options.
- Take Snapshots
  - Before you start testing any tools or malware, always take a snapshot of your VM.
  - Snapshots allow you to restore the machine to a previous, clean state if something goes wrong.

- How to Take Snapshots in VirtualBox:
  - In the VM’s settings, go to Snapshots, and click Take Snapshot. Label it appropriately for easy identification.

IMAGE

# Generating Telemetry from Malicious Activity
Once the lab environment is set up, we can simulate an attack scenario to generate telemetry data for analysis. This project highlights offensive security techniques, including using Nmap for port reconnaissance, creating custom malware, and analyzing telemetry generated after executing the malware with Windows Defender disabled. While antivirus evasion is not a focus, the project emphasizes telemetry generation and analysis, enabling a deeper understanding of offensive and defensive cybersecurity techniques.

# Tools & Techniques:
- Nmap: For port scanning and service identification on the target machine.
- MsfVenom: To create a reverse shell malware payload.
- Metasploit Framework: To manage and monitor reverse shell connections.
- Sysmon: For detailed system activity logging.
- Splunk: To ingest and analyze telemetry logs from Sysmon.

# Skills Demonstrated:
- Port scanning and reconnaissance using Nmap.
- Malware creation and execution with offensive security tools.
- Configuring and managing Sysmon for telemetry generation.
- Using Splunk for log ingestion, analysis, and creating actionable insights.
- Understanding the relationship between offensive actions and defensive monitoring techniques.

# Step-by-Step Process
## Using Nmap for reconnaissance 
- I focus on using Nmap to scan a Windows machine effectively, employing options like '-a' for comprehensive scans and '-Pn' to bypass pings, ultimately identifying open ports such as RDP on port 3389.
-  Using Nmap to scan the target Windows machine for open ports, specifically looking for services such as RDP on port 3389.
  - This emphasizes the importance of generating whether the ports are open and annotating any findingss.
    IMAGE 
## Creating and Executing Malware
- msfvenom is provided to generate basic malware ( though this clarifies that it won't cover methods to evade antivirus detection extensively. Instead, the primary goal is to showcase telemetry generation on the Windows machine.) 

- Simulate malicious activity by crafting and executing basic malware by using MsfVenom to create a reverse shell payload configured with custom LHOST and LPORT settings.
IMAGE
- Set up a Metasploit handler from Metasploit Framwork to capture connections from the executed malware.
IMAGE

## Downloading and Running the Malware
- Disable Windows Defender on the target machine to allow malware execution.
  - Open Windows Security > Virus & Threat Protection > Manage Settings > Turn Off Real-Time Protection.
IMAGE
- Host the malware on an HTTP server for download.
  -Host the malware for download (e.g., using a simple HTTP server with Python)
IMAGE 
- Download and execute the malware on the target machine, confirming the reverse shell connection using netstat and to task manager.
  IMAGE

## Monitoring Telemetry with Splunk
- Install and configure Sysmon on the Windows machine to capture detailed logs of system activities.
- Use Splunk to ingest Sysmon logs and create an index for endpoint telemetry.
- Analyze logs to detect malicious activity and visualize key IoCs with Splunk dashboards.
IMAGE

## Conclusion

- This project demonstrates the combination of setting up a secure home lab with simulating malicious activity to generate and analyze telemetry. It helps develop skills in offensive security, malware analysis, and defensive monitoring techniques. By using tools like Nmap, Metasploit, Sysmon, and Splunk, you’ll gain a deeper understanding of how malicious activity can be detected and how telemetry data can be used to enhance cybersecurity defense strategies.

