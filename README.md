# Vulnerable-Machine-Bluemoon: 2021
Walkthrough for the Bluemoon: 2021 CTF Lab task from VulnHub by using Kali Linux.


## Lab Environment

* **Attacker OS:** Kali Linux (IP: 192.168.56.103)
* **Target OS:** BlueMoon (IP: 192.168.56.101) 
* **Virtualization:** Oracle VirtualBox (VB)

## System Hacking Stages

### 1. Reconnaissance

We start with knowing our (attacker) ip address first:

```bash
ifconfig
```

Next, I used **netdiscover** to locate the target's IP:

```
sudo netdiscover
```

For more detail, I used **nmap -sn [Network Address]**
```bash
nmap -sn 192.168.56.0/24
```

### 2. Scanning

Once the target is identified, I used **nmap** to find open ports and services

```bash
nmap -sC -sV -p- 192.168.56.101
```

Then we do **dirb** scanning

```bash
dirb http://192.168.56.101 ~/Desktop/wordlist.txt -X .php,.html,.txt
```
Once I successfully scanninng, open Firefox and try to search http://[Target's IP]

Proceed to do **gobuster** scanning after knowing there have an open port.

```bash
gobuster dir -u http://192.168.50.101 --wordlist /usr/share/disbuster/worlists/directory-list-2.3-medium.txt
```


