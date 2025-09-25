Task Five — Nmap Scan of Metasploitable

Author: Vaishnav K R
GitHub: https://github.com/vaish-git926
Email: krvyshnav095@gmail.com

Overview

This repository contains the results of a network reconnaissance task (Task Five). I installed Metasploitable (v2), ran an Nmap scan of all ports from a Kali host, and saved the output here for review.

Files

taskfive_nmap_fast.txt — Optional fast scan (-F -sV) (if present).

README.md — This file.
Environment & Credentials

Host OS: VirtualBox on Windows (your host)

Target VM: Metasploitable 2 (prebuilt vulnerable VM)

Username: msfadmin

Password: msfadmin

Attacker VM: Kali Linux (VirtualBox)

Recommended network: Host-Only (both VMs) or NAT Network so Kali ⇄ Metasploitable can communicate.
How I imported Metasploitable (quick)

Downloaded Metasploitable2 .vmdk (~825 MB) from SourceForge.

In VirtualBox: New → Type: Linux, Version: Ubuntu (32-bit) → Use existing virtual hard disk and select the .vmdk.

VM Settings:

System → Disable EFI

Boot order → Hard Disk first

Network → Adapter 1: Host-Only Adapter (or NAT Network)

Start VM and login with msfadmin/msfadmin.

Run ip a / ifconfig inside the VM to get the target IP.
How to reproduce the scan

On Kali (replace <IP> with Metasploitable IP):

Fast scan (quick):nmap -F -sV <IP> -oN taskfive_nmap_fast.txt
Full/complete scan (all ports, more discovery):nmap -p- -A <IP> -oN taskfive_nmap.txt
Notes:

-p- scans ports 1–65535.

-A enables OS detection, version detection, default scripts and traceroute.

Add -T4 to speed up if your network/VM resources allow.
Pushing results to this repo

If you generated taskfive_nmap.txt locally, push with:git init
git add taskfive_nmap.txt
git commit -m "Add nmap scan output for Task Five"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/taskfive.git
git push -u origin main
Use a GitHub personal access token (PAT) if HTTPS prompts for a password.

Notes & Safety

Metasploitable is intentionally vulnerable — do not expose it to the public Internet.

Use Host-Only or isolated NAT networks to avoid accidentally attacking other hosts.

This VM is for lab use only; do not run production services on it.
Troubleshooting

VM shows No bootable medium: ensure .vmdk/.vdi is attached as a Hard Disk and EFI is disabled.

If nmap cannot reach the target: verify both VMs are on the same Host-Only or NAT Network and check IPs via ip a.

If the disk is tiny (few MB) the download is corrupt — re-download the 825MB VMDK or the OVA.
Contact

Vaishnav K R — krvyshnav095@gmail.com
LinkedIn: www.linkedin.com/in/vaishnav-k-r-35a474285
License

This repository is provided for learning and lab purposes. No license — use at your own risk.
