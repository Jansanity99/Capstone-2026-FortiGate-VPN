# Capstone 2026 - Secure Enterprise Network

## Overview
Implementation of a secure enterprise network with site-to-site VPN, remote access VPN, and centralized security monitoring using Splunk.

## Network Topology

| Device | Site | IP Address | Role |
|--------|------|-----------|------|
| FW1 (FortiGate 60E) - LAN | A | 192.168.10.1/24 | Site A LAN Gateway |
| FW1 (FortiGate 60E) - WAN | A | 10.0.0.1/30 | VPN Endpoint |
| Host PC 1 / Splunk SIEM | A | 192.168.10.2 | Log Collection / SIEM |
| Ubuntu Attacker | A | 192.168.10.10 | Attack Machine |
| FW2 (FortiGate-B) - LAN | B | 192.168.20.1/24 | Site B LAN Gateway |
| FW2 (FortiGate-B) - WAN | B | 10.0.0.2/30 | VPN Endpoint |
| Host PC 2 | B | 192.168.20.2 | Site B End User |
| Ubuntu Server (Target) | B | 192.168.20.10 | Target / Victim Server |
| SSL VPN Client Pool | Remote | 10.212.134.200-210 | Remote User VPN IPs |

## What Was Implemented
- [DONE] Site-to-Site IPsec VPN (IKEv2, AES-256, SHA-256, DH Group 14)
- [DONE] Client-Based SSL VPN with FortiClient portal (port 10443)
- [DONE] Centralized logging with Splunk Enterprise 9.0.0.1
- [DONE] Fortinet FortiGate App for Splunk dashboards
- [DONE] Attack simulation: Nmap port scan + SSH brute force with Hydra
- [DONE] Attack detection and analysis in Splunk
  ## Repository Structure

  | Folder | Contents |
  |--------|---------|
  | 01-topology | Network diagram |
  | 02-fw1-siteA | FW1 screenshots and config |
  | 03-fw2-siteB | FW2 screenshots and config |
  | 04-vpn | IPsec VPN setup and verification |
  | 05-ssl-vpn | SSL VPN setup and test |
  | 06-splunk | Splunk setup, searches, dashboard |
  | 07-attacks | Nmap and Hydra attack screenshots |
  | 08-configs | Sanitized FortiGate config backups |

  ## VPN Configuration

  | Parameter | Value |
  |-----------|-------|
  | VPN Type | IPsec Site-to-Site |
  | IKE Version | 2 |
  | Encryption | AES-256 |
  | Authentication | SHA-256 |
  | DH Group | 14 |
  | Phase 1 Lifetime | 86400 sec |
  | Phase 2 Lifetime | 43200 sec |
  | SSL VPN Port | 10443 |
  | Syslog Port | UDP 514 |

  ## Technologies Used

  - FortiGate (FortiOS 7.0) x2
  - Splunk Enterprise 9.0.0.1
  - Fortinet FortiGate App for Splunk
  - Nmap, Hydra
  - Ubuntu Linux (Attacker + Target)
    ## Attack Simulation

    | Attack | Tool | Source | Target | Detection |
    |--------|------|--------|--------|-----------|
    | Port Scan | Nmap | 192.168.10.10 | 192.168.20.0/24 | High volume multi-port connections from single IP |
    | SSH Brute Force | Hydra | 192.168.10.10 | 192.168.20.10:22 | Repeated port 22 connections from single IP |

    ---
    *Capstone Project 2026 | Cybersecurity Program*

    ## AWS connectivity to Fortigate

    <img width="1287" height="648" alt="image" src="https://github.com/user-attachments/assets/98dcf6bb-6824-4d38-b574-0ea8af2ae432" />
    <img width="1322" height="277" alt="image" src="https://github.com/user-attachments/assets/4ab28109-a248-4d0b-9949-adfa182c98fe" />

