# Basic Home Lab for Cybersecurity
This repository documents the setup and configuration of a basic home lab tailored for learning and practicing cybersecurity concepts. The lab environment provides a hands-on platform to explore fundamental skills such as vulnerability assessment, network monitoring, and ethical hacking, as well as to test tools and techniques in a controlled environment.

# Goals
<b>Learn by Doing </b>: Gain practical experience with cybersecurity tools and techniques.
<b>Safe Experimentation</b>: Test exploits, analyze malware, and practice defense strategies without impacting live systems.
<b>Skill Development</b>: Enhance skills in areas like penetration testing, digital forensics, and incident response.


# Tool used
- Oracle Virtualbox
- Windows 10 (using tools like Microsoft Defender, Event viewer and installed Sysmon and Splunk) 
- Kali linux (using other tools like Nmap, Metasploit and Python) 


# Lab Components
## Hardware
- Personal computer or laptop with virtualization support (Intel VT-x/AMD-V).
- Minimum 16GB RAM (recommended for smooth virtualization).

## Software & Tools
- Virtualization Platform: VirtualBox by Oracle.
- Operating Systems:
  - Kali Linux (offensive security tools).
  - Windows 10/11 (to practice privilege escalation and malware analysis).
  - Ubuntu/Debian (to set up a vulnerable Linux server).
- Vulnerable Applications:
  - DVWA (Damn Vulnerable Web Application).
  - Metasploitable 2 or 3.
- Monitoring Tools:
  - Wireshark (network analysis).
  - Splunk Free or ELK Stack (log analysis).
- Other Tools:
  - Nmap, Burp Suite, and Nessus Essentials (vulnerability scanning).
## Network Setup
- Simulated network with isolated virtual machines in VirtualBox for safe experimentation.
- Configured VirtualBox network settings for segmentation and security (e.g., NAT, Host-Only, and Bridged adapters).
- Configure Static IP on Windows 10
  - Locate the Host-Only Network Adapter (e.g., "Ethernet 2"), right-click it, and select Properties.
  - Select Internet Protocol Version 4 (TCP/IPv4) and click Properties.
  - Enter the following:
    - IP Address: 192.168.56.102
    - Subnet Mask: 255.255.255.0
    - Default Gateway: 192.168.56.1
  - Click OK to save the settings.
- Configure Static IP on Kali Linux
  - Open the terminal in Kali Linux.
  - Edit the network configuration file

- Test Connectivity with Ping
  - On Kali Linux, ping the Windows 10 machine
  - On Windows 10, ping the Kali Linux machine
    - If the ping command succeeds, you will see replies indicating connectivity.
## Activities & Scenarios
- Vulnerability Scanning: Use Nmap and Nessus to discover and assess vulnerabilities.
- Penetration Testing: Perform basic exploits using Metasploit and manual techniques.
- Network Traffic Analysis: Capture and analyze packets with Wireshark.
- Log Analysis: Set up a log monitoring system using Splunk or ELK.
- Forensics: Practice analyzing compromised systems.

# Important Considerations
## Sandbox Environment
Setting up a virtual machine (VM) does not automatically create a sandboxed environment. Without proper configuration, malicious software running in the VM could potentially infect your host system or other devices on your network.

## Recommendations:
- Do Not Run Untrusted Malware: Avoid downloading and executing malware from the internet until you are certain your environment is fully isolated.
- Controlled Malware Testing: Use tools like Kali Linux to craft your own malware or exploits. Test these in a controlled setup to learn how they behave without risking unintended consequences.
- Network Isolation: Configure VirtualBox network settings (e.g., Host-Only or NAT network modes) to isolate your virtual machines from your home network.

<b><ins>Pro Tip:</b></ins> 
Improperly configured virtual machines can lead to serious issues. For example, running ransomware in an unprotected VM could result in data loss on your host system. Always double-check your configuration before executing potentially harmful operations.

## Snapshots
A snapshot is a "moment-in-time" backup of your VM that you can revert to later. This is a crucial tool for safe experimentation in your home lab.

- Best Practices for Snapshots:
  - Create a Snapshot Before Testing: Always create a snapshot before running exploits, malware, or any potentially destructive operations.
  - Revert When Needed: If your VM becomes unusable due to testing, revert to the snapshot to restore your system to a functional state.
  - Neat Organization: Label your snapshots clearly, such as "Pre-Malware Test" or "Fresh Install".

- How to Create a Snapshot in VirtualBox:
  - Right-click your virtual machine in the VirtualBox Manager.
  - Select Take Snapshot.
  - Provide a descriptive name and optional notes for future reference.
    - By using snapshots effectively, you can safely experiment and learn without permanent damage to your lab environment.

#  Generate telemetry and detect malicious activity on a target machines.
- This project highlights offensive security techniques, including using Nmap for port scanning, creating custom malware, and analyzing telemetry generated after executing the malware with Windows Defender disabled.
- While not focused on antivirus evasion methods, the project prioritizes showcasing telemetry generation on a Windows machine, enabling exploration of various approaches to enhance cybersecurity skills.

-This project simulates a real-world attack scenario to generate telemetry data and analyze malicious activity on a Windows target machine. The process includes using Nmap for reconnaissance, creating and executing custom malware, and monitoring system telemetry with tools like Sysmon and Splunk. While antivirus evasion is not a focus, the project emphasizes telemetry generation and analysis, enabling a deeper understanding of offensive and defensive cybersecurity techniques.

# Objective:   
- Simulate malicious activity on a Windows machine to generate telemetry data.
- Analyze telemetry logs to detect malicious behaviors and improve understanding of security monitoring techniques.

# Tools & Techniques:
- Nmap: For port scanning and service identification on the target machine.
- MsfVenom: To create a reverse shell malware payload.
- Metasploit Framework: To manage and monitor reverse shell connections.
- Sysmon: For detailed system activity logging.
- Splunk: To ingest and analyze telemetry logs from Sysmon.

# Outcome:
- Generated detailed telemetry from simulated malware activity.
- Detected key indicators of compromise (IoCs) using Splunk dashboards and queries.
- Gained insights into how telemetry data can enhance defensive strategies.

# Skills Demonstrated:

- Port scanning and reconnaissance using Nmap.
- Malware creation and execution with offensive security tools.
- Configuring and managing Sysmon for telemetry generation.
- Using Splunk for log ingestion, analysis, and creating actionable insights.
- Understanding the relationship between offensive actions and defensive monitoring techniques.

# Step-by-Step Process
## Using Nmap for Scanning
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
This comprehensive approach demonstrates offensive techniques, highlights their impact on system telemetry, and fosters expertise in detecting and analyzing malicious activity in a simulated environment.


