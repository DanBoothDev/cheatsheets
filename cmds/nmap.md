# NMAP CheatSheet

## Overview
- [Detecting OS](#detect-os)
- [Using a different DNS server](#different-dns-server)
- [traceroute](#traceroute)
- [Scan to file](#scan-to-file)


## Detect OS
```bash
nmap -O $IP
# OR
nmap --osscan-guess $IP
```

## Different DNS server
```bash
nmap --dns-servers 8.8.8.8 1.1.1.1
```

## Traceroute
```bash
sudo nmap --traceroute $IP
```

## Scan to file
```bash
mkdir nmap
nmap -sC -sV -oN nmap/$IP.log $IP
```
