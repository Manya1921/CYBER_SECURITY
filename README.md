# CYBER_SECURITY

## Objective
Perform basic network reconnaissance on an authorized host, identify open ports, and document findings and remediation suggestions.

> *Important:* All scanning was performed only on devices/networks I own or have explicit permission to test.

## Environment
- Scanner: Nmap v7.98 
- Target IP: 192.168.245.61
- Date: 2025-10-20

## Methodology
1. Identify local network and the target IP.
2. Run a TCP SYN scan to discover open ports.
3. Perform service/version detection and safe NSE scripts to gather service details and possible vulnerabilities.
4. Save outputs and analyze results.
5. Document findings and suggest remediation.

## Commands used
```bash
# Quick SYN scan (discover open ports)
nmap -sS 192.168.245.61 -oN scans/nmap_quick_scan.txt

# Detailed scan: service/version, OS detection, default safe scripts, all ports
nmap -sS -sV -O --script "default or safe" -p 1-65535 192.168.245.61 -oN scans/nmap_detailed_scan.txt

# SMB-specific checks (targeting SMB ports)
nmap -p445 --script smb-os-discovery,smb-security-mode,smb-vuln* -sV 192.168.245.61 -oN scans/nmap_smb_scan.txt
