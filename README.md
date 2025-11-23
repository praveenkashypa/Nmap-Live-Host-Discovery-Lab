# Nmap-Live-Host-Discovery-Lab
This project is based on the Nmap Live Host Discovery practical lab from TryHackMe. The objective of this lab is to explore multiple techniques used to identify active hosts on a network before performing deeper reconnaissance or exploitation activities.

# Overview
Network reconnaissance always begins by determining which hosts are alive and reachable. Nmap provides several powerful host discovery methods that can bypass firewalls, packet filtering, or ICMP restrictions. This lab focuses on the following techniques:

# ARP Scan

ICMP (Ping Sweep) Scans

TCP Ping Scans

# UDP Ping Scans

Techniques & Commands Used
ARP Scan
ARP Scanning is effective and reliable on Local Area Networks (LANs). It directly queries MAC addresses on the same broadcast domain.

nmap -PR

Purpose: Detect hosts on the same network segment even when ICMP is blocked.

ICMP Scanning (Ping Sweeps)
These scans test whether hosts respond to ICMP requests.

Scan Type Option Description Echo Request -PE Standard ping test Timestamp Request -PP Checks time-based responses Address Mask Request -PM Retrieves subnet mask of the target

Example:

nmap -PE

⚠️ Downside: If ICMP is blocked by firewall rules, results may be incomplete.

TCP Ping Scans
Used when ICMP fails. TCP responses indicate that a host is live.

Example using common accepted ports:

nmap -PS80,443 # SYN Ping Scan

nmap -PA80,443 # ACK Ping Scan

Useful when only specific TCP ports are allowed through perimeter filters.

UDP Ping Scans
Some services respond to UDP probes (like DNS on port 53).

nmap -PU53

Helps reveal hosts even when TCP is filtered.

# Scanning Options Summary
Scan Method Useful When Command Example ARP Scan Local LAN environment nmap -PR 192.168.1.0/24 ICMP Sweep ICMP not filtered nmap -PE TCP Ping Scan ICMP blocked nmap -PS80,443 UDP Ping Scan TCP filtered nmap -PU53

# Key Learning Outcomes
✔ Host discovery is the first step of successful network recon ✔ ARP is most accurate and fastest on LANs ✔ Varying scan types helps bypass firewalls and filters ✔ Combining techniques provides the most reliable results

# 🧩 Tools Used

Nmap

Kali Linux / AttackBox (TryHackMe)

This lab improved my understanding of how reconnaissance works in real-world penetration testing scenarios. By mastering multiple host discovery methods, we can ensure accurate mapping of potential attack surfaces before enumeration or exploitation.
