# Vulnerability Management Lab

This repository contains the step-by-step guide for setting up a **Windows 10 virtual machine** in **Azure**, performing vulnerability scans with **Tenable Nessus Professional**, making the system intentionally vulnerable, remediating it, and visualizing scan results.

---

## Table of Contents

1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Creating the Azure VM](#creating-the-azure-vm)
4. [Configuring the Windows 10 Environment](#configuring-the-windows-10-environment)
5. [Running Vulnerability Scans](#running-vulnerability-scans)

   * [Scan 1](#run-scan-1)
   * [Making the VM Vulnerable](#make-virtual-machine-vulnerable)
   * [Scan 2](#run-scan-2)
   * [Remediating the System](#remediate-the-system)
   * [Scan 3](#run-scan-3)
6. [Data Visualization](#data-visualization)
7. [References](#references)

---

## Overview

This lab demonstrates **vulnerability management** by:

* Setting up a Windows 10 VM in Azure
* Installing and configuring **Nessus Professional**
* Running multiple scans before and after introducing vulnerabilities
* Remediating vulnerabilities and validating system security
* Visualizing scan data for analysis

---

## Prerequisites

* Azure subscription
* Work or school email to register for **Tenable Nessus Professional** (a custom ProtonMail with domain can be used)
* Remote Desktop Connection (RDP)
* Basic knowledge of Windows administration

---

## Creating the Azure VM

1. **Configure the Basics Tab:**

   * Resource group: `VulnerabilityManagement`
   * VM name: `vm-lab`
   * Region: `US East 2`
   * Image: Windows 10 Pro, 22H2 x64 Gen2
   * Size: Standard D2s v3 (2 vCPUs, 8 GiB memory)
   * Administrator credentials: Enter secure credentials

2. **Disks Tab:** Standard HDD (locally-redundant storage)

3. **Networking Tab:** Enable *Delete public IP and NIC when VM is deleted*

4. **Monitoring Tab:** Disable boot diagnostics

5. **Review + Create Tab:** Create VM

---

## Configuring the Windows 10 Environment

1. Connect via **Remote Desktop Connection**
2. Pause **Windows Update** immediately
3. Install **Nessus Professional**
4. Configure **Windows Defender Firewall**:

   * Run `wf.msc`
   * Modify settings for **Domain, Private, Public** profiles
5. Configure **PowerShell settings**:

   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" -Name "LocalAccountTokenFilterPolicy" -Value 1 -Type DWord -Force
   ```
6. Restart the VM

---

## Running Vulnerability Scans

### Run Scan 1

1. Open **Nessus Professional** → *Create new scan* → *Advanced Scan*
2. Configure scan:

   * Name: `Vulnerability_Management_Demo`
   * Target: VM private IP (example: `10.1.0.4`)
   * Enable *Use fast network discovery*
3. Add credentials:

   * Windows admin credentials
4. Enable services during scan:

   * Remote Registry
   * Administrative shares
   * Server service
5. Start scan

---

### Make Virtual Machine Vulnerable

* Install **Firefox version 110**

---

### Run Scan 2

* Execute second vulnerability scan using the same settings

---

### Remediate the System

1. Remove vulnerabilities:

   * Uninstall Firefox v110
2. Install secure software (optional):

   * Latest Firefox version
   * Enable automatic updates

---

### Run Scan 3

* Perform final vulnerability assessment to ensure remediation success

---

## Data Visualization

* Use the provided Excel document to create **graphs and charts** comparing the three scans
* Visualize trends, vulnerabilities fixed, and remaining risks

---

## References

* [Tenable Nessus Professional](https://www.tenable.com/products/nessus)
* [Microsoft Azure VM Documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/)
* [Windows Defender Firewall](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/)

---

I can also make a **more visually structured version with badges, diagrams, and color-coded steps** so it looks professional on GitHub if you want.

Do you want me to create that enhanced version?
