# virtual-network-traffic-analysis-lab
A virtual network lab using Ubuntu, Kali Linux, Wireshark, and VirtualBox for packet analysis.
✅ README.md — Virtual Network Traffic Analysis Lab
# Virtual Network Traffic Analysis Lab  
**Author:** Farhan Muntasir  
**Project Date:** 2025  
**Tools:** VirtualBox, Ubuntu, Kali Linux, Wireshark

---

## 📌 Overview
This project demonstrates how to build a virtual network lab using **VirtualBox** and analyze network traffic between two virtual machines (Ubuntu + Kali Linux) using **Wireshark**.  
The following protocols were captured and analyzed:

- **ARP** – Address Resolution Protocol  
- **ICMP** – Ping / Connectivity  
- **DNS** – Domain Resolution  
- **HTTP** – Web Traffic  

This lab provides foundational skills for cybersecurity, penetration testing, and network engineering.

---

## 🖥️ Lab Environment

### **Virtual Machines**
| VM | OS | Purpose |
|----|----|---------|
| Ubuntu | Ubuntu 22.04 | Wireshark packet capture |
| Kali Linux | Kali Live | Generate traffic (ping, DNS, browsing) |

### **Network Configuration**
Two adapters were used in VirtualBox:

- **Host-Only Adapter** → Internal traffic (Ubuntu ↔ Kali)  
- **NAT Adapter** → Internet access for DNS + HTTP  

---

## ⚙️ Wireshark Installation (Ubuntu)

```bash
sudo apt update
sudo apt install wireshark
sudo usermod -aG wireshark $USER
sudo reboot


After reboot, Wireshark can capture packets without sudo.

🧪 Commands Used in the Lab
🔹 Connectivity Testing (ICMP)

Kali → Ubuntu

ping 192.168.56.102


Ubuntu → Kali

ping 192.168.56.20

🔹 Network Interface Check

Ubuntu:

ip a


Kali:

ip addr show

🔹 DNS Resolution

Ubuntu:

nslookup google.com
nslookup yahoo.com
nslookup testphp.vulnweb.com
dig ubuntu.com


Kali:

nslookup google.com

🔹 HTTP Traffic

Visit from Ubuntu browser:

http://testphp.vulnweb.com
http://example.com


Optional CLI test:

curl http://example.com

🔹 Flush DNS Cache (Ubuntu)
sudo systemd-resolve --flush-caches

🔍 Wireshark Filters Used
arp
icmp
dns
http
tcp


These filters helped isolate specific protocol traffic.

📡 Protocol Analysis Summary
1️⃣ ARP – Address Resolution Protocol

ARP determines MAC addresses for IP communication.

“Who has?” and “is-at” packets appear before ICMP.

Enables hosts to communicate on the same network.

2️⃣ ICMP – Ping / Connectivity

Kali generated ping traffic; Ubuntu captured echo request/reply.

Response time measured connectivity.

ICMP verifies host reachability.

3️⃣ DNS – Domain Resolution

Ubuntu sent DNS queries to public DNS servers via NAT.

DNS responses contained IPs for requested domains.

Demonstrates how domain names become IP addresses.

4️⃣ HTTP – Web Traffic

Visiting an HTTP website generated GET requests.

Wireshark captured unencrypted HTTP headers.

Showed full request/response behavior.

🧾 Summary of Findings
Protocol	Purpose	Result
ARP	MAC Address Discovery	Successful
ICMP	Connectivity Check	Successful
DNS	Domain Lookup	Successful
HTTP	Web Communication	Successful
✅ Conclusion

This virtual network lab successfully demonstrated:

How VMs communicate over Host-Only and NAT networks

How to capture and analyze network packets

How common protocols behave in real environments

How Ubuntu + Kali can be used for practical cybersecurity labs

This project builds essential skills for:

Network engineers

SOC analysts

Pentesters

Cybersecurity students
