# Setting Up a Home Lab for Cybersecurity
## Project Overview
This project combines setting up a secure home lab environment for cybersecurity testing with generating and analyzing telemetry from simulated malicious activity. 
The goal is to experiment with offensive techniques and detect malicious behaviors using monitoring tools, such as Sysmon and Splunk. By combining VM configuration, malware creation, and telemetry analysis, this project offers a comprehensive learning experience.



## Table of Contents
1. Introduction
2. Setting up the Home Lab
3.  Network Configuration for Secure Testing
4.  Generating Telemetry from Malicious Activity
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

  <img src="https://i.imgur.com/iQyWFYh.png" height="80%" width="60%" alt="Virtual box"/>

- Verify the SHA-256 Hash: Ensure the downloaded file is legitimate by checking its hash against the official value.

  <img src="https://i.imgur.com/M6S1OTF.png" height="90%" width="90%" alt="Virtual box"/>

  <img src="https://i.imgur.com/VtwhJnV.png" height="80%" width="60%" alt="Virtual box"/>

  <img src="https://i.imgur.com/ptaOtad.png" height="60%" width="60%" alt="Virtual box"/>

- Complete the Installation: Follow the installation prompts and customize any settings as needed.
  

## Creating Virtual Machines (VMs)
- Windows 10 VM:
  - Use the Media Creation Tool to create a Windows 10 ISO and set up a VM with at least 4GB RAM and 2 CPUs.
- Kali Linux VM:
  - Download a pre-built Kali Linux ISO from Kali.org and set up a VM for penetration testing tools.

  <img src="https://i.imgur.com/6Z6G2ZD.png" height="50%" width="50%" alt="Virtual box"/>

  <img src="https://i.imgur.com/7ZtdJ6T.png" height="50%" width="50%" alt="Virtual box"/>

  <img src="https://i.imgur.com/2i8emPg.png" height="50%" width="50%" alt="Virtual box"/>

  <img src="https://i.imgur.com/l5mrdwK.png" height="50%" width="50%" alt="Virtual box"/>

# 3. Network Configuration for Secure Testing
VirtualBox offers several network modes to control how your VMs communicate with each other and the host system. The correct configuration is essential for securing your testing environment, especially when working with potentially malicious software.

## Network Options in VirtualBox
- <b>NAT</b>: Default setting, gives the VM access to the internet but isolates it from the host network. Ideal for tool testing.
- <b>NAT Network</b>: Allows multiple VMs to share the same network while maintaining internet access.
- <b>Bridged</b>: The VM acts like a physical device on your local network. Not recommended for malware analysis as it increases the risk of compromising the host.
- <b>Host-Only</b>: Only allows communication between the host and VMs. No internet access.
- <b>Internal Network</b>: Isolates the VM network from the host and the internet. Best for malware analysis as VMs can communicate only with each other.
- <b>Not Attached</b>: No network connection. Ideal for maximum isolation.

## Step-by-Step Configuration Guide for setting up your VMs and configuring network settings:
- Create a new VM for Windows 10 or Kali Linux.
- Assign sufficient resources (RAM, CPU, storage) based on your system’s capabilities.
- Choose Network Settings:
  - <ins>For testing tools</ins>, select <b>NAT</b>.
  - <ins>For malware analysis</ins>, select <b>Internal Network</b> or <b>Not Attached</b> .

 <img src="https://i.imgur.com/AZKFdhW.png" height="50%" width="50%" alt="Network Options"/>

- Configure static IP addresses for VM communication (e.g., use ipconfig in Windows and ifconfig in Kali).

  <img src="https://i.imgur.com/dXsZWx6.png" height="30%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/FZK1m6J.png" height="30%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/WrLXr7L.png" height="30%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/FuDMxl1.png" height="30%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/imJrxVK.png" height="30%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/PFIagfz.png" height="30%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/cCZYSln.png" height="30%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/se9KAnT.png" height="30%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/WVD6RlY.png" height="30%" width="50%" alt="Network Options"/>
  

- Take a snapshot after configuring the VM to preserve the setup.
   

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

    <img src="https://i.imgur.com/nK9AacH.png" height="50%" width="50%" alt="Network Options"/>
      


# 4. Generating Telemetry from Malicious Activity
Once the lab environment is set up, we can simulate an attack scenario to <b>generate telemetry data</b> for analysis. This project highlights offensive security techniques, including using <b>Nmap</b> for port <b>reconnaissance</b>, creating custom <b>malware</b>, and analyzing telemetry generated after executing the malware with <b>Windows Defender disabled</b>. While <b>antivirus</b> evasion is not a focus, the project emphasizes telemetry generation and analysis, enabling a deeper understanding of <b>offensive and defensive cybersecurity techniques</b>.

# Tools & Techniques:
- <b>Nmap</b>: For port scanning and service identification on the target machine.
- <b>MsfVenom</b>: To create a reverse shell malware payload.
- <b>Metasploit Framework</b>: To manage and monitor reverse shell connections.
- <b>Sysmon</b>: For detailed system activity logging.
- <b>Splunk</b>: To ingest and analyze telemetry logs from Sysmon.

# Skills Demonstrated:
- Port scanning and <b>reconnaissance</b> using <b>Nmap</b>.
- Malware creation and execution with offensive security tools.
- Configuring and managing Sysmon for telemetry generation.
- Using <b>Splunk</b> for log ingestion, analysis, and creating actionable insights.
- Understanding the relationship between <b>offensive actions and defensive monitoring techniques</b>.

# Step-by-Step Process
## Using Nmap for reconnaissance 

- I focus on using <b>Nmap</b> to scan a Windows machine effectively, employing options like '<b>-a</b>' for comprehensive scans and '<b>-Pn</b>' to bypass <b>pings</b>, ultimately identifying open ports such as <b>RDP on port 3389</b>.
  - This emphasizes the importance of generating whether the ports are open and annotating any findingss.

    <img src="https://i.imgur.com/StwSUwf.png" height="50%" width="50%" alt="Network Options"/>
    
    <img src="https://i.imgur.com/AZKFdhW.png" height="50%" width="50%" alt="Network Options"/>


## Creating and Executing Malware
- <b>msfvenom</b> is provided to generate basic malware ( though this clarifies that it won't cover methods to evade antivirus detection extensively. Instead, the primary goal is to showcase telemetry generation on the Windows machine.) 

- Simulate malicious activity by crafting and executing basic malware by using <b>MsfVenom</b> to create a reverse shell payload configured with custom <b>LHOST</b> and <b>LPORT</b> settings.

- The payload is designed to leverage the Meterpreter reverse TCP exploit, masquerading as an innocent-looking file named resume.pdf.exe.
  - Purpose of the Name "resume.pdf.exe"
    - The name resume.pdf.exe is deliberately misleading. It tricks potential victims into believing the file is a harmless PDF document, potentially their resume, while it is actually an executable malware file.
   - Verification of Payload
     - After generating the file, commands like ls and file ensure the payload is created and confirm its properties.
-  Handler Setup in Metasploit
    - Handler is configured to listen for connections from the infected machine.
    - The payload in the handler is set to match the one used during the msfvenom process:
       - windows/x64/meterpreter/reverse_tcp.
  
  <img src="https://i.imgur.com/AZKFdhW.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/FnfEeGS.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/4YMA3HU.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/HjmO6Z0.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/sNj8wiN.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/5C07RN3.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/LXtxNvK.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/DXhFL5p.png" height="50%" width="50%" alt="Network Options"/>
  


## Downloading and Running the Malware
- Disable Windows Defender on the target machine to allow malware execution.
  - <b>Open Windows Security > Virus & Threat Protection > Manage Settings > Turn Off Real-Time Protection.</b>
- Host the malware on an HTTP server for download.
  - Host the malware for download (e.g., <b>using a simple HTTP server with Python</b>)
    
  <img src="https://i.imgur.com/uhI3KD6.png" height="50%" width="50%" alt="Network Options"/>

- Download and execute the malware on the target machine, confirming the reverse shell connection using netstat and to task manager.
  
  <img src="https://i.imgur.com/mfZMHNQ.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/AtMzF2c.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/i0ofA3o.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/rUNPhRz.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/yG6MQl1.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/ISyKHeg.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/PyQh0LP.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/o0AfrPN.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/6OXRhXt.png" height="50%" width="50%" alt="Network Options"/>
  


## Monitoring Telemetry with Splunk
- Install and configure Sysmon on the Windows machine to capture detailed logs of system activities.
- Use Splunk to ingest Sysmon logs and create an index for endpoint telemetry.
- Analyze logs to detect malicious activity and visualize key IoCs with Splunk dashboards.

  <img src="https://i.imgur.com/IMFxPeW.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/LF7BS9S.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/tchPfbh.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/tSslrg2.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/UcDlGg1.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/FNZVlS6.png" height="50%" width="50%" alt="Network Options"/>
  
  <img src="https://i.imgur.com/0wRApAq.png" height="50%" width="50%" alt="Network Options"/>
  

## 5. Conclusion

- This project demonstrates the combination of setting up a secure home lab with simulating malicious activity to generate and analyze telemetry. It helps develop skills in offensive security, malware analysis, and defensive monitoring techniques. By using tools like Nmap, Metasploit, Sysmon, and Splunk, you’ll gain a deeper understanding of how malicious activity can be detected and how telemetry data can be used to enhance cybersecurity defense strategies.

