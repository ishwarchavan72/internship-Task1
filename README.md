Task 1: Scan Your Local Network for Open Ports

Objective:
Learn to identify open ports on devices in your local network to understand network exposure and potential risks.

Tools Used:
- Nmap for scanning open ports
- Wireshark for packet capture analysis

My Network Details:
-local Network Range Scanned: 192.168.225.0/24

Steps Performed:

1. Installed Nmap
From: [https://nmap.org](https://nmap.org)

2. Identified Local Network Range
Using:bash
ipconfig    # (on Windows)

3. Discovered Live Hosts
nmap -sn 192.168.225.0/24

4. Scanned for Open Ports
nmap -sS 192.168.225.0/24

5. Captured Traffic in Wireshark 
Filtered using - 
 ip.addr == 192.168.225.81

 Open Port Analysis : 


  IP              Port 	    Service           Description                   		 
 192.168.225.1      80      HTTP              Web interface                	     
 192.168.225.1     6666     IRC              IRC chat service (uncommon)     
 192.168.225.1     7777     CBT              Custom service (unknown)         
 192.168.225.81     135     MSRPC            Windows RPC                     	
 192.168.225.81     139     NetBIOS-SSN      File sharing                 
 192.168.225.81     445     Microsoft-DS     SMB file sharing                
 192.168.225.81     3306    MySQL            Database server         


Risks Identified:
- SSH port open on LAN
  → Remote access service that can be targeted if weak credentials are used
- NetBIOS ports exposed (139/445)
  → Used for file sharing; may leak sensitive data or allow lateral movement
- HTTP service accessible on some devices
  → Could expose admin interfaces or outdated web applications
- IRC and unknown service on port 7777
  → Uncommon services that may indicate outdated or insecure software

 Recommended Actions for Risks : 
- Restrict SSH access and use key-based authentication
- Disable NetBIOS/SMB if not required on devices
- Limit HTTP services to trusted IPs; test for vulnerabilities
- Investigate unknown ports (e.g., 7777) and shut them down if unneeded

 Key Concepts Learned:
- Port scanning
- TCP SYN scan
- CIDR and subnetting
- Network reconnaissance
- Service exposure analysis


 Task Completed
  Date: 2025-08-04
