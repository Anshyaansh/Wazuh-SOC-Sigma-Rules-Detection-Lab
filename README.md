# 🛡️ Wazuh SOC Sigma-Rules | Detection Lab

**Author:** Devansh Jaiswal

Welcome to **MiniSOC**, a live-fire threat detection laboratory designed to simulate, detect, and analyze common adversary techniques. This project moves beyond static theory, providing a fully functional environment where custom Sigma and Wazuh rules catch simulated attacks in real time. 

This repository contains hand-written detection rules mapped directly to the **MITRE ATT&CK®** framework, accompanied by execution proofs and a complete guide to recreating the infrastructure.

---

## 🏗️ Lab Architecture

The environment relies on a host-only and NAT networking setup to securely isolate the attacks while allowing log forwarding. 

*   **SIEM / Defensive Engine:** Ubuntu 22.04 running Wazuh Manager 
    *   *IP Address:* `192.168.56.105`
*   **Victim Machine:** Windows 10 Pro running Wazuh Agent & Sysmon
    *   *IP Address:* `192.168.56.104`

> **Note:** Sysmon is configured on the Windows endpoint to capture granular process creation, network connections, and file modifications, which are then shipped to the Wazuh server for analysis against our custom rules.

---

## 📁 Repository Structure

The project is organized to separate the infrastructure setup, the detection engineering logic, and the proof of execution:
```text
📦 MiniSOC-Active-Defense
 ┣ 📂 Setup                 # Detailed lab configuration and networking guides
 ┣ 📂 sigma-rules           # Raw, portable Sigma rules for SIEM deployment
 ┗ 📂 Attack & Detection    # Screenshots and logs proving the alerts fired
    ┣ 📂 powershell nop     # PowerShell obfuscation attack proofs
    ┣ 📂 volume shadow copy # Ransomware precursor attack proofs
    ┣ 📂 attack recon       # Post-compromise discovery proofs
    ┣ 📂 schedule tasks     # Persistence mechanism proofs
    ┗ 📂 wevtutil           # Defense evasion (log clearing) proofs
