# 🛡️ Purple Team Lab Scenario 2: Initial Access Execution Persistence Detection

📌 Project Overview

This project demonstrates a multi-stage purple team attack simulation performed in a home lab using Kali Linux, Windows Server, and Wazuh SIEM. The objective was to emulate common adversary techniques and validate that security monitoring tools successfully detected each phase of the attack.

🎯 Objectives

🔍 Perform reconnaissance against a Windows target
🔑 Simulate an initial access attempt using Remote Desktop Protocol (RDP)
⚙️ Execute commands on the Windows system
📌 Simulate a persistence technique
📁 Trigger File Integrity Monitoring (FIM)
📊 Investigate alerts generated in Wazuh

🖥️ Lab Environment

Component
Technology
Attacker Machine
Kali Linux
Target Machine
Windows Server
SIEM
Wazuh
Log Collection
Wazuh Agent
Attack Framework
MITRE ATT&CK


⚔️ Attack Chain

🔍 Phase 1 – Reconnaissance
Objective
Discover open ports and running services on the Windows server.
Command
nmap -sS -sV 192.168.1.15

Result

Identified open network ports
Enumerated running services
Simulated attacker reconnaissance
Detection
Windows Firewall logs (if enabled)
Network activity within Wazuh
Possible scan detection rules
📷 Screenshot


<img width="621" height="442" alt="Screenshot 2026-06-28 120247" src="https://github.com/user-attachments/assets/3f876d42-c627-4fb6-a1ad-68530704b3e8" />


🔑 Phase 2 – Initial Access

Objective
Simulate a failed Remote Desktop login.
Command
xfreerdp /v:192.168.1.15 /u:FakeAdmin

Result

Failed authentication attempt
Generated Windows Security Event ID 4625
Detection
✅ Failed Logon
✅ Password Guessing Alert
✅ Source IP Address
📷 Screenshots

<img width="1883" height="827" alt="Screenshot 2026-06-28 122709" src="https://github.com/user-attachments/assets/83a6e9ff-5cbb-4b60-96b7-e4b0230f0078" />














<img width="1008" height="619" alt="Screenshot 2026-06-28 123255" src="https://github.com/user-attachments/assets/96470108-840f-4729-9c04-1ff3ecf8a0d4" />














<img width="839" height="688" alt="Screenshot 2026-06-28 123155" src="https://github.com/user-attachments/assets/99fd3da5-0448-490d-948d-6237ec36c2d7" />
















<img width="766" height="808" alt="Screenshot 2026-06-28 124653" src="https://github.com/user-attachments/assets/9fe904f7-68a8-4963-a26a-a5555674a766" />









⚙️ Phase 3 – Execution

Objective
Execute commands on the Windows server.
Commands
whoami
ipconfig
Get-Process

Result

Generated Windows process activity
Created PowerShell logs (if enabled)
Detection
Process execution
PowerShell activity
Sysmon Event ID 1 (if configured)
📷 Screenshot

















<img width="1143" height="940" alt="Screenshot 2026-06-28 133026" src="https://github.com/user-attachments/assets/3dcb0027-c5de-4dc0-be04-49579b1df902" />

















<img width="1782" height="591" alt="Screenshot 2026-06-28 133806" src="https://github.com/user-attachments/assets/d9dc87a6-8b9f-4817-bba4-f31c8bf1b260" />



📌 Phase 4 – Persistence

Objective
Simulate persistence using a Registry Run Key.
Command
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v TestApp /t REG_SZ /d notepad.exe

Result

Created a registry startup entry that launches Notepad when the user logs in.
Detection
Registry modification
Startup persistence
Wazuh monitoring
📷 Screenshot


<img width="1134" height="184" alt="Screenshot 2026-06-28 142022" src="https://github.com/user-attachments/assets/5c7409ea-952d-4c62-92a3-f64dd1e4e6b0" />









<img width="1448" height="65" alt="Screenshot 2026-06-28 142713" src="https://github.com/user-attachments/assets/6d5cea58-816b-4368-85e9-d0237d7566db" />


📁 Phase 5 – File Integrity Monitoring (FIM)

Objective
Trigger File Integrity Monitoring by creating a new file.
Command
echo "attack simulation" > C:\PurpleTeamLab\testfile.txt

Result

Created a monitored file
Triggered Wazuh FIM
Detection
✅ File Created
✅ File Modified
📷 Screenshot




<img width="1909" height="940" alt="Screenshot 2026-06-28 184139" src="https://github.com/user-attachments/assets/2e5f0de7-c181-497e-8bfc-d980f30bbdc4" />














<img width="1875" height="734" alt="Screenshot 2026-06-28 184408" src="https://github.com/user-attachments/assets/ef71aaaf-8de9-4d28-b749-b56ab9c71dfe" />













<img width="551" height="766" alt="Screenshot 2026-06-29 070848" src="https://github.com/user-attachments/assets/f4f119c7-b415-4cf5-b63e-7aa6bddecc0b" />












<img width="543" height="778" alt="Screenshot 2026-06-29 070934" src="https://github.com/user-attachments/assets/bcffdc1a-b399-489a-9844-33ef20f787d6" />














<img width="680" height="745" alt="Screenshot 2026-06-29 070341" src="https://github.com/user-attachments/assets/9eaf86e6-b694-4cb0-8a34-2a9a9b196371" />



📊 Investigation Timeline

Time
Activity
Detection
10:01
🔍 Nmap Scan
Network Activity
10:03
🔑 Failed RDP Login
Event ID 4625
10:05
⚙️ PowerShell Execution
Process Logs
10:07
📌 Registry Persistence
Registry Modification
10:09
📁 File Created
FIM Alert


🎯 MITRE ATT&CK Mapping

Technique
ATT&CK ID
Active Scanning
T1595
Brute Force
T1110
PowerShell
T1059.001
Process Discovery
T1057
System Information Discovery
T1082
Registry Run Keys / Startup Folder
T1547.001


🛡️ Wazuh Detection Summary

✅ Reconnaissance Activity
✅ Failed Authentication Attempts
✅ Windows Security Event Logs
✅ Process Execution
✅ Registry Changes
✅ File Integrity Monitoring

📚 Skills Demonstrated

🛡️ Security Monitoring
🔎 Threat Hunting
📊 SIEM Analysis
🪟 Windows Event Log Analysis
🐉 Kali Linux
⚡ Nmap
🔐 RDP Authentication Analysis
📁 File Integrity Monitoring
🎯 MITRE ATT&CK Mapping
🔍 Incident Investigation

🚀 Lessons Learned

This lab demonstrated how a SIEM can correlate activity across multiple stages of an attack. By simulating reconnaissance, initial access, execution, persistence, and file changes, I validated detection capabilities within Wazuh and strengthened my understanding of attacker behavior, Windows event logging, and security monitoring.

📸 Screenshots

📷 Nmap Scan
📷 Failed RDP Login
📷 Windows Event ID 4625
📷 Wazuh Authentication Alert
📷 PowerShell Execution
📷 Registry Persistence
📷 File Integrity Monitoring Alert


👩‍💻 Author

Michael Stromer

Aspiring SOC Analyst | Blue Team | Detection Engineering | Threat Hunting

