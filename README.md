Cyber Security Internship – Task 1
📌 Objective

To perform basic network reconnaissance by scanning the local network using Nmap and analyzing the TCP SYN packets using Wireshark. 
This helps in understanding how open ports expose services on devices and how attackers use port scanning as a reconnaissance technique.

🛠 Tools Used

- Kali Linux – Penetration testing OS
- Nmap – Network and port scanning tool
- Wireshark – Packet capturing and analysis

🌐 My Network Setup

- IP Address: 10.0.2.15
- Subnet: 10.0.2.0/24
- Interface Used: eth0

🔎 Nmap Commands Used

1. Discover Live Hosts:
    sudo nmap -sn 10.0.2.0/24

2. TCP SYN Port Scan:
    sudo nmap -sS 10.0.2.0/24

3. Save Output to File:
    sudo nmap -sS 10.0.2.0/24 -oN scan_results.txt

📄 Nmap Scan Summary

4 devices were detected on the subnet:

10.0.2.2 – Ports 135 (MSRPC), 445 (Microsoft-DS)
10.0.2.3 – Ports 135 (MSRPC), 445 (Microsoft-DS)
10.0.2.4 – Ports 135 (MSRPC), 445 (Microsoft-DS)
10.0.2.15 – Port 80 (HTTP - My machine)

🛡 Risk Analysis

Port 135 (MSRPC): Vulnerable to remote code execution attacks.
Port 445 (Microsoft-DS): Often targeted by SMB exploits like EternalBlue.
Port 80 (HTTP): Web services may leak sensitive information or allow exploits.

🧪 Wireshark Packet Capture

Filter Used:
    tcp.flags.syn == 1 && tcp.flags.ack == 0

This captures SYN packets during the Nmap TCP SYN scan.

Screenshot: wireshark_syn_scan.jpg (uploaded to GitHub repo)

✅ Outcome

- Learned to scan a local network for live devices and open ports.
- Understood how SYN scanning works and identified the traffic in Wireshark.
- Documented risks associated with open services.
- Successfully organized the findings and pushed the report to GitHub.

📁 Files in this Repository

- scan_results.txt – Raw Nmap scan output
- wireshark_syn_scan.jpg – Screenshot of captured SYN packets
- README.md – Task documentation file

🧪 Additional Evidence: Wireshark .pcapng File

The file `wireshark.pcapng` contains the raw network traffic captured using Wireshark during the execution of an Nmap TCP SYN scan.
This file provides low-level packet data, which can be further analyzed to understand how Nmap interacts with hosts on the network.

To analyze:
1. Open `wireshark.pcapng` in Wireshark.
2. Apply the following display filter:
       tcp.flags.syn == 1 && tcp.flags.ack == 0
3. Observe the SYN packets sent from the scanning machine (10.0.2.15) to multiple target IPs (e.g., 10.0.2.2, 10.0.2.3).
4. Look for ports such as 135, 445, and 80 in the destination fields to correlate with scan results.

This file is included in the repository for deeper inspection and as verifiable evidence of network reconnaissance activity.

