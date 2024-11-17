# Basic Home Lab for Cybersecurity
Overview
This repository documents the setup and configuration of a basic home lab tailored for learning and practicing cybersecurity concepts. The lab environment provides a hands-on platform to explore fundamental skills such as vulnerability assessment, network monitoring, and ethical hacking, as well as to test tools and techniques in a controlled environment.

Goals
Learn by Doing: Gain practical experience with cybersecurity tools and techniques.
Safe Experimentation: Test exploits, analyze malware, and practice defense strategies without impacting live systems.
Skill Development: Enhance skills in areas like penetration testing, digital forensics, and incident response.
Lab Components
1. Hardware
Personal computer or laptop with virtualization support (Intel VT-x/AMD-V).
Minimum 16GB RAM (recommended for smooth virtualization).
2. Software & Tools
Virtualization Platform: VirtualBox by Oracle.
Operating Systems:
Kali Linux (offensive security tools).
Windows 10/11 (to practice privilege escalation and malware analysis).
Ubuntu/Debian (to set up a vulnerable Linux server).
Vulnerable Applications:
DVWA (Damn Vulnerable Web Application).
Metasploitable 2 or 3.
Monitoring Tools:
Wireshark (network analysis).
Splunk Free or ELK Stack (log analysis).
Other Tools:
Nmap, Burp Suite, and Nessus Essentials (vulnerability scanning).
3. Network Setup
Simulated network with isolated virtual machines in VirtualBox for safe experimentation.
Configured VirtualBox network settings for segmentation and security (e.g., NAT, Host-Only, and Bridged adapters).
Activities & Scenarios
Vulnerability Scanning: Use Nmap and Nessus to discover and assess vulnerabilities.
Penetration Testing: Perform basic exploits using Metasploit and manual techniques.
Network Traffic Analysis: Capture and analyze packets with Wireshark.
Log Analysis: Set up a log monitoring system using Splunk or ELK.
Forensics: Practice analyzing compromised systems.
