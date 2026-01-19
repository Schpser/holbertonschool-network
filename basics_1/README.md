# 🌐 Holberton School - Network Basics 1

Welcome to **Network Basics 1**! 🎉 This project focuses on practical network configuration, localhost operations, IP address manipulation, and network service monitoring. You'll learn to configure network interfaces, work with localhost, and monitor network ports and services. ✨

---

## 📋 Tasks Overview

| Task | Description |
|------|-------------|
| [`0-change_your_home_IP`](./0-change_your_home_IP) | 🏠 Script to configure localhost and domain resolution |
| [`1-show_attached_IPs`](./1-show_attached_IPs) | 📡 Display all active IPv4 addresses on the machine |
| [`2-port_listening_on_localhost`](./2-port_listening_on_localhost) | 👂 Script that listens on port 98 on localhost |

---

## 🎯 Concepts Covered

- ✅ **Localhost**: Understanding 127.0.0.1 and loopback interface
- ✅ **0.0.0.0**: The "any" address and its special meaning
- ✅ **/etc/hosts**: Local DNS resolution configuration
- ✅ **Active Network Interfaces**: Identifying and displaying network interfaces
- ✅ **IPv4 Addresses**: Extracting and working with IP addresses
- ✅ **Network Listening**: Creating services that listen on specific ports
- ✅ **Netcat**: Using nc for network operations
- ✅ **IP Configuration**: Modifying system network settings

## 🎓 Learning Objectives

> 💡 By the end of this project, you should be able to:

- 🏠 Explain what localhost/127.0.0.1 is and why it's special
- 🌐 Understand the meaning of 0.0.0.0 in network context
- ✍️ Modify the `/etc/hosts` file to configure local DNS
- 🔍 Display all active IPv4 addresses on your machine
- 👂 Create a listening service on a specific port
- 🛠️ Use netcat (nc) for network operations
- 🔧 Understand the loopback interface
- 📝 Write Bash scripts for network configuration
- 🔒 Understand localhost security implications
- 🚀 Test network services locally

## ⚙️ Requirements

### General
- 🐧 Ubuntu 20.04 LTS or later
- 🛠️ Basic knowledge of Linux command line
- 🔧 Network utilities: `ifconfig`, `ip`, `nc` (netcat)
- ✍️ All files should end with a new line
- 📝 All Bash scripts must be executable (`chmod +x`)
- 🔍 Scripts must pass `shellcheck` without errors
- ⚡ All scripts should start with `#!/usr/bin/env bash`
- 💬 Second line of scripts should be a comment explaining what the script does

---

## 🛠️ Setup & Installation

#### 1. Install Required Tools
```bash
# Update package index
sudo apt-get update

# Install network tools (if not already installed)
sudo apt-get install -y net-tools netcat

# Verify netcat installation
nc -h

# Check ifconfig availability
ifconfig -a
```

#### 2. Verify Current Configuration
```bash
# Check current localhost resolution
ping -c 2 localhost

# View current /etc/hosts file
cat /etc/hosts

# Display all IP addresses
hostname -I

# Show all network interfaces
ip addr show
```

---

## 🚀 Usage

#### Understanding Localhost
```bash
# Localhost is 127.0.0.1 (IPv4) or ::1 (IPv6)
ping -c 2 127.0.0.1

# All addresses in 127.0.0.0/8 are loopback addresses
ping -c 2 127.0.0.2
ping -c 2 127.1.2.3

# Test localhost resolution
nslookup localhost
```

#### Working with /etc/hosts
```bash
# View the hosts file
cat /etc/hosts

# Backup before modifying (IMPORTANT!)
sudo cp /etc/hosts /etc/hosts.backup

# Edit hosts file (requires sudo)
sudo nano /etc/hosts

# Format: IP_ADDRESS  hostname [aliases...]
# Example:
# 127.0.0.1    localhost
# 192.168.1.100    myserver.local myserver
```

#### Display IP Addresses
```bash
# Show all network interfaces
ip addr show

# Display only IPv4 addresses
ip -4 addr show | grep inet

# Extract IP addresses only
hostname -I

# Show specific interface
ifconfig eth0
```

#### Listening on Ports
```bash
# Listen on port 98 using netcat
nc -l 98

# Listen on localhost only
nc -l 127.0.0.1 98

# Test connection to a listening port
# (in another terminal)
nc localhost 98
# or
telnet localhost 98
```

#### Running the Scripts
```bash
# Make scripts executable
chmod +x 0-change_your_home_IP
chmod +x 1-show_attached_IPs
chmod +x 2-port_listening_on_localhost

# Run script to change localhost resolution
sudo ./0-change_your_home_IP

# Display all IPv4 addresses
./1-show_attached_IPs

# Start listening on port 98
./2-port_listening_on_localhost
```

---

## 📊 Network Configuration Quick Reference

```
┌────────────────────────────────────────────────┐
│          🌐 Important IP Addresses            │
├────────────────────────────────────────────────┤
│  127.0.0.1      │ Localhost (loopback)        │
│  0.0.0.0        │ All interfaces / any address│
│  127.0.0.0/8    │ Loopback network range      │
│  ::1            │ IPv6 localhost              │
│  Private ranges │ 10.0.0.0/8                  │
│                 │ 172.16.0.0/12               │
│                 │ 192.168.0.0/16              │
└────────────────────────────────────────────────┘
```

## 🔑 Common Localhost Uses

| Use Case | Description |
|----------|-------------|
| **Development** | Test web servers without exposing to network |
| **Database** | Connect to local database instances |
| **API Testing** | Test APIs before deployment |
| **Port Forwarding** | Tunnel services through SSH |
| **Security** | Restrict services to local access only |
| **Debugging** | Monitor local network traffic |

---

## 🏠 Understanding Localhost & 127.0.0.1

**Localhost** is a hostname that refers to the current computer. It resolves to:
- **127.0.0.1** (IPv4)
- **::1** (IPv6)

The **loopback interface** allows a computer to communicate with itself without using physical network hardware.

### Why Use Localhost?

✅ **Security**: Services are not exposed to the network  
✅ **Speed**: No physical network overhead  
✅ **Development**: Test applications locally  
✅ **Reliability**: Always available, no network dependency  

### 0.0.0.0 vs 127.0.0.1

| Address | Meaning | Usage |
|---------|---------|-------|
| **0.0.0.0** | All available interfaces | Server listening on all IPs |
| **127.0.0.1** | Loopback only | Server only accessible locally |

```bash
# Listen only on localhost (secure)
nc -l 127.0.0.1 8080

# Listen on all interfaces (accessible from network)
nc -l 0.0.0.0 8080
```

---

## 📚 Resources

### Official Documentation
- [Netcat Manual](https://man7.org/linux/man-pages/man1/nc.1.html)
- [hosts(5) Man Page](https://man7.org/linux/man-pages/man5/hosts.5.html)
- [IP Command Cheat Sheet](https://access.redhat.com/sites/default/files/attachments/rh_ip_command_cheatsheet_1214_jcs_print.pdf)

### Learning Materials
- [Understanding Localhost](https://en.wikipedia.org/wiki/Localhost)
- [The /etc/hosts File](https://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/)
- [Loopback Interface](https://www.cloudflare.com/learning/network-layer/what-is-localhost/)

### Tools & Utilities
- [Netcat (nc)](https://netcat.sourceforge.net/)
- [iproute2 Package](https://wiki.linuxfoundation.org/networking/iproute2)
- [net-tools](https://sourceforge.net/projects/net-tools/)

### Additional Reading
- 📖 [../Notions.md](../Notions.md) - Complete networking concepts guide
- 📖 [../basics_0/README.md](../basics_0/README.md) - Network fundamentals

---

## 🧪 Practice Commands

```bash
# 1. Test localhost connectivity
ping -c 4 localhost
ping -c 4 127.0.0.1

# 2. View current hosts file
cat /etc/hosts

# 3. Show all IP addresses
hostname -I

# 4. Display IPv4 addresses only
ip -4 addr show scope global | grep inet | awk '{print $2}' | cut -d/ -f1

# 5. Check what's listening on ports
sudo netstat -tulpn | grep LISTEN

# 6. Test if a port is in use
nc -zv localhost 98

# 7. Start a simple server on port 8080
while true; do echo -e "HTTP/1.1 200 OK\n\nHello" | nc -l 8080; done

# 8. Check loopback interface
ip addr show lo
```

---

## 🔍 Troubleshooting Tips

| Issue | Solution |
|-------|----------|
| **Can't modify /etc/hosts** | Use `sudo` to edit system files |
| **Port already in use** | Check with `sudo netstat -tulpn \| grep :PORT` |
| **localhost not resolving** | Verify /etc/hosts has `127.0.0.1 localhost` |
| **nc command not found** | Install: `sudo apt-get install netcat` |
| **Permission denied on port < 1024** | Use `sudo` for privileged ports |
| **Changes don't apply** | Some services cache DNS, restart them |

---

## ⚠️ Important Notes

- 🔐 **Always backup** `/etc/hosts` before modifying: `sudo cp /etc/hosts /etc/hosts.backup`
- 🚨 **Use sudo carefully** when modifying system configuration files
- 🔒 **Ports below 1024** require root/sudo privileges to bind
- 💡 **Test changes** carefully before committing permanent modifications
- 🔄 **Restore backup** if something goes wrong: `sudo cp /etc/hosts.backup /etc/hosts`

---

**Happy Networking! 🌐🚀**