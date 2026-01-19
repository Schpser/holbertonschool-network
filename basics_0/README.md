# 🌐 Holberton School - Network

Welcome to the **Holberton School Network** project! 🎉 This repository is designed to teach you the fundamentals of computer networking. You will learn about network protocols, the OSI model, IP addressing, routing, and essential networking concepts that form the backbone of modern internet communications. ✨

---

## 📋 Tasks Overview

| Task | Description |
|------|-------------|
| [`0-OSI_model`](./basics_0/0-OSI_model) | 📚 Understanding the OSI Model layers |
| [`1-types_of_network`](./basics_0/1-types_of_network) | 🌐 Different types of networks (LAN, WAN, etc.) |
| [`2-MAC_and_IP_address`](./basics_0/2-MAC_and_IP_address) | 🔑 MAC and IP addressing concepts |
| [`3-UDP_and_TCP`](./basics_0/3-UDP_and_TCP) | 🔄 Transport layer protocols comparison |
| [`4-TCP_and_UDP_ports`](./basics_0/4-TCP_and_UDP_ports) | 🚪 Understanding network ports |
| [`5-is_the_host_on_the_network`](./basics_0/5-is_the_host_on_the_network) | 🏹 Network connectivity testing script |

---

## 🎯 Concepts Covered

- ✅ **OSI Model**: The 7 layers of network architecture
- ✅ **TCP/IP Model**: Practical implementation of networking protocols
- ✅ **IP Addressing**: IPv4, IPv6, subnetting, and CIDR notation
- ✅ **MAC Addresses**: Physical addressing and ARP protocol
- ✅ **Protocols**: TCP, UDP, HTTP, HTTPS, DNS, DHCP, ICMP
- ✅ **Network Types**: LAN, WAN, WLAN, MAN, PAN
- ✅ **Network Equipment**: Routers, switches, hubs, gateways
- ✅ **Ports & Services**: Well-known ports and their applications
- ✅ **Security**: Firewalls, NAT, VPN, encryption
- ✅ **Troubleshooting**: Network diagnostic tools and methodologies

## 🎓 Learning Objectives

> 💡 By the end of this project, you should be able to:

- 🗣️ Explain the OSI model and its 7 layers
- 🔄 Differentiate between TCP and UDP protocols
- ✍️ Configure and understand IP addresses (IPv4 and IPv6)
- 🏹 Use network diagnostic tools (ping, traceroute, netstat)
- ✨ Understand subnetting and CIDR notation
- 🔑 Explain how DNS, DHCP, and ARP work
- 📦 Identify network equipment and their functions
- 🚀 Troubleshoot common network issues
- 🔒 Understand basic network security concepts
- 🌍 Explain the difference between public and private IP addresses

## ⚙️ Requirements

### General
-   🐧 Ubuntu 20.04 LTS or later
-   🛠️ Basic knowledge of Linux command line
-   🔧 Network utilities: `ping`, `traceroute`, `netstat`, `ip`, `ifconfig`
-   ✍️ All files should end with a new line
-   📝 All Bash scripts must be executable
-   🔍 Scripts must pass `shellcheck` without errors

---

## 🛠️ Setup & Installation

#### 1. Install Network Tools
```bash
# Update package index
sudo apt-get update

# Install essential network tools
sudo apt-get install -y net-tools iputils-ping traceroute dnsutils netcat

# Install advanced monitoring tools (optional)
sudo apt-get install -y iftop nethogs tcpdump wireshark
```

#### 2. Verify Installation
```bash
# Check network interfaces
ip addr show
# or
ifconfig

# Test connectivity
ping -c 4 8.8.8.8

# Check DNS resolution
nslookup google.com

# Display routing table
ip route show
```

---

## 🚀 Usage

#### Basic Network Commands
```bash
# Display IP configuration
ip addr show

# Show routing table
ip route show

# Test connectivity (ping)
ping -c 5 google.com

# Trace route to destination
traceroute google.com

# Display network connections
netstat -tunlp
# or modern alternative
ss -tunlp

# DNS lookup
nslookup example.com
dig example.com

# Display ARP table
arp -a
ip neigh show
```

#### Network Troubleshooting
```bash
# Test if a port is open
telnet example.com 80
# or
nc -zv example.com 80

# Monitor network traffic
sudo tcpdump -i eth0

# Check bandwidth usage
iftop -i eth0

# View active connections by process
sudo nethogs
```

#### Running Network Scripts
```bash
# Make script executable
chmod +x script_name.sh

# Run the script
./script_name.sh

# Example: Ping script
./0-OSI_model/ping_test.sh 8.8.8.8
```

---

## 📊 Network Layers Quick Reference

```
┌─────────────────────────────────────────────────┐
│              🌐 OSI Model (7 Layers)            │
├─────────────────────────────────────────────────┤
│  7️⃣ Application  │ HTTP, FTP, SSH, DNS         │
│  6️⃣ Presentation │ SSL/TLS, JPEG, ASCII         │
│  5️⃣ Session      │ NetBIOS, RPC                │
│  4️⃣ Transport    │ TCP, UDP                    │
│  3️⃣ Network      │ IP, ICMP, Routing           │
│  2️⃣ Data Link    │ Ethernet, MAC, Switch       │
│  1️⃣ Physical     │ Cables, Hubs, Signals       │
└─────────────────────────────────────────────────┘
```

## 🔑 Common Ports Reference

| Port | Service | Protocol |
|------|---------|----------|
| 20/21 | FTP | TCP |
| 22 | SSH | TCP |
| 23 | Telnet | TCP |
| 25 | SMTP | TCP |
| 53 | DNS | TCP/UDP |
| 80 | HTTP | TCP |
| 443 | HTTPS | TCP |
| 3306 | MySQL | TCP |
| 3389 | RDP | TCP |

---

## 📚 Resources

### Official Documentation
- [TCP/IP Guide](http://www.tcpipguide.com/)
- [RFC Documents (IETF)](https://www.ietf.org/standards/rfcs/)
- [Cisco Networking Basics](https://www.cisco.com/c/en/us/solutions/small-business/resource-center/networking/networking-basics.html)

### Learning Materials
- [OSI Model Explained](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)
- [Subnet Calculator](https://www.subnet-calculator.com/)
- [IP Address Guide](https://www.iplocation.net/ip-address)

### Tools & Utilities
- [Wireshark - Network Protocol Analyzer](https://www.wireshark.org/)
- [Netcat - TCP/IP Swiss Army Knife](https://nc110.sourceforge.io/)
- [Speedtest - Internet Speed Test](https://www.speedtest.net/)

### Additional Reading
- 📖 [Notions.md](./Notions.md) - Complete networking concepts guide in French
- 🖼️ [Pictures/](./Pictures/) - Network diagrams and visual aids

---

## 🧪 Practice Commands

```bash
# 1. Check your local IP address
ip addr show | grep inet

# 2. Find your default gateway
ip route | grep default

# 3. Test DNS resolution
nslookup google.com
dig google.com +short

# 4. Check all listening ports
sudo netstat -tunlp | grep LISTEN

# 5. Trace the path to a website
traceroute -n google.com

# 6. Display active network connections
ss -tupn

# 7. Show network statistics
netstat -s

# 8. Monitor real-time traffic
sudo iftop -i eth0
```

---

## 🔍 Troubleshooting Tips

| Issue | Command to Diagnose |
|-------|---------------------|
| **No internet connection** | `ping 8.8.8.8` (test connectivity) |
| **DNS not working** | `nslookup google.com` (test DNS) |
| **Slow network** | `ping -c 10 google.com` (check latency) |
| **Port not accessible** | `telnet host port` or `nc -zv host port` |
| **Unknown IP conflicts** | `arp -a` (check ARP table) |

---

**Happy Networking! 🌐🚀**