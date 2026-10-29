
# 🔒 Cybersecurity Lab Environment Setup
> *Building an isolated virtual lab for penetration testing and ethical hacking practice*5

| Type | Lab Specifications & Provenance |
| :--- | :--- |
| **🛡️ Core Focus** | `Skill Cybersecurity` • `Penetration Testing` • `Ethical Hacking` |
| **⚙️ Platform** | `Virtualbox v7.2` • `Skill Virtualization` |
| **🐧 OS & Net** | `Kali Linux v2026.2` • `Kali Linux` • `Skill Linux` • `10.0.0.0/24` |
| **👤 Credits** | Student: `Ayesha Irshad` • Instructor: `Waqas Karim CCIE` |
| **🌐 Source** | `GitHub` • `NetworkWalks` |

---

## 📌 Project Overview
This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

---

## 🎯 Objectives
The main objectives of this project are to:

* Install and configure VirtualBox.
* Install/import Kali Linux as a virtual machine.
* Create a private NAT Network for the cybersecurity lab.
* Configure network connectivity for Kali Linux.
* Assign a consistent IP address to the Kali VM.
* Verify network connectivity and DNS resolution.
* Take a clean VM snapshot for recovery.
* Document the complete setup process.
* Prepare the environment for future cybersecurity projects.

---

## 🛡️ Purpose of the Lab
The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

* Network reconnaissance.
* Port scanning.
* Vulnerability assessment.
* Packet analysis.
* Web security testing.
* Exploitation practice.
* Security-tool experimentation.

---

> [!WARNING]
> This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

---

## 🏗️ Lab Architecture

---

<img width="955" height="539" alt="1-screenshot-title-image png" src="https://github.com/user-attachments/assets/1d718848-c299-4fba-af8c-b118140201cc" />

Additional target machines can be added to the same virtual network in future projects.

---

## ⚙️ Lab Configuration

### 🌐 System Configuration & Network Matrix

| Deployment Layer | Host Environment | Core Hypervisor | Target Endpoint | Segment Routing & DNS |
| :--- | :--- | :--- | :--- | :--- |
| **Active Specifications** | Windows 10 <br>• Intel Core i5 <br>• 8 GB RAM | VirtualBox 7.2 | Kali Linux 2026.2 <br>• 2048 MB Memory Allocation | **Subnet:** `10.0.0.0/24` <br>**Gateway:** `10.0.0.1` <br>**DNS Resolver:** `8.8.8.8` |
| **Static Addressing** | — | **Network Mode:** Private NAT | **Assigned Node IP:** `10.0.0.2/24` | **Reserved DHCP Pool:** `10.0.0.3 – 10.0.0.99` |

---

## 🪜 Lab Setup Procedure

The following sequential process documents the environmental deployment, hypervisor configuration, and static routing allocations required to bring the security lab to an active state.

---

<details>
<summary><b>📦 Step 1. Install 7-Zip</b></summary>

### Objective
Provision the required file compression architecture to decompress target virtual machine payloads.
* **Core Dependency:** `7-Zip Archiver`
* **Execution Role:** Extracting compressed `.7z` virtual disk packages securely without data corruption.

</details>

---

<details>
<summary><b>🖥️ Step 2. Install VirtualBox</b></summary>

### Objective
Deploy the primary hardware virtualization engine to orchestrate guest instances.
* **Core Dependency:** `Oracle VirtualBox v7.x`
* **Execution Role:** Serves as the base hypervisor platform hosting isolated sandbox clusters.

</details>

---

<details>
<summary><b>🌐 Step 3. Create the NAT Network</b></summary>

### Objective
Establish an isolated, software-defined network boundary inside the hypervisor fabric.
* **Routing Topology:** <kbd>Private NAT Network</kbd>

> * **Network Name:** <kbd>NatNetwork</kbd>
> * **IPv4 Prefix:** <kbd>10.0.0.0/24</kbd>
> * **DHCP Scope:** <kbd>Enabled</kbd>
> * **IPv6 Stack:** <kbd>Disabled</kbd>


  <img width="959" height="509" alt="2-screenshot-network-settings-1 png" src="https://github.com/user-attachments/assets/60ff6831-94d1-43c6-928c-51de307effde" />

---

> [!NOTE]
> A NAT Network topology was selected over a standard configuration to establish a multi-machine ecosystem. This allows multiple concurrent virtual machines to maintain secure node-to-node communication while simultaneously inheriting outbound WAN connectivity paths.


</details>

---

<details>
<summary><b>👾 Step 4. Import Kali Linux</b></summary>

### Objective
Import and map the primary penetration testing guest node into the provisioned sandbox network.
* **Target Node Platform:** `kali.org`

* **Memory Allocation:** <kbd>2048 MB RAM</kbd>

### Software-Defined Hardware Mapping
* **Adapter 1:** Attached to $\rightarrow$ `NAT Network` (`NatNetwork`)
* **Adapter Type:** `Intel PRO/1000 MT Desktop`
* **Host Interfacing:** Configured custom shared directories for secure file translation between host-to-guest layers.

  <img width="959" height="538" alt="3-screenshot-kali-linux png" src="https://github.com/user-attachments/assets/ffd608cb-fd06-4f0f-bedb-f6307b9542f2" />

</details>

---

<details>
<summary><b>⚙️ Step 5. Configure the Kali Linux Network</b></summary>

### Objective
Stabilize network architecture by overriding transient properties with permanent parameters.
* **Provisioning Logic:** Static mapping guarantees persistent node reachability during active security simulations.

### Configured Operational Profile
* **IP Address:** <kbd>10.0.0.2</kbd>
* **Subnet Mask:** <kbd>255.255.255.0</kbd>
* **Gateway:** <kbd>10.0.0.1</kbd>
* **DNS:** <kbd>8.8.8.8</kbd>

</details>

---

<details>
<summary><b>🛡️ Step 6. Create a Clean VM Snapshot</b></summary>

### Objective
Engineer an immutable rollback vector to protect laboratory assets against volatile payloads or configuration degradation.
* **Example Snapshot Name:** `My Kali-Linux`
* **Operational Intent:** Establishes a known-good environmental baseline, enabling instant system remediation and recovery.

</details>

---
# 🔎 Environment Verification & Diagnostic Log

The following diagnostic suite ensures all network pathways, static allocations, core binaries, and system baselines are functioning correctly within the sandboxed segment.

| Evaluation Metric | Diagnostic Command Execution | Target Success State |
| :--- | :--- | :--- |
| **🌐 Interface Addressing** | `ip a` | Confirm static allocation matches `10.0.0.2/24` |
| **🚨 Edge Gateway Route** | `ping -c 4 10.0.0.1` | Receive 100% successful ICMP echo replies |
| **🌍 WAN Routing Link** | `ping -c 4 8.8.8.8` | Verify operational egress through NAT routing |
| **🎯 Name Resolution** | `nslookup networkwalks.com` | DNS resolver maps external domains successfully |
| **🧰 Binary Audit (Nmap)** | `nmap --version` | Validate core reconnaissance package runtime |
| **⏳ State Preservation** | `Revert Baseline Snapshot` $\rightarrow$ `ip a` | Confirm environment rolls back to pristine state |

**Example Results**

---

> * **Interface Target:** <kbd>10.0.0.2/24</kbd>
> * **Routing Transit:** <kbd>10.0.0.1</kbd> (NAT Gateway)
> * **Name Resolution:** <kbd>8.8.8.8</kbd> (Public DNS)

---

## 🐞 Incident Management & Troubleshooting Log

Documenting engineering bottlenecks and deployment remedies is a critical phase of infrastructure implementation. Expand the drop-down elements below to review the encountered errors and their respective remediation workflows.

<details>
<summary><b>🔧 Incident 1.0: Loss of Internet Connectivity Post-Static IP Allocation</b></summary>

### Root Cause Analysis
Upon establishing manual IPv4 static parameters, outbound WAN routing failed due to interface negotiation delays within the network daemon stack.

### Remediation Protocol & Workaround
To bypass interface handshaking delays, the Duplicate Address Detection (DAD) timeout threshold was suppressed directly via the network management engine:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

---

> [!NOTE]
> Network interface descriptors vary across hardware distributions. System administrators must query active interfaces to determine their explicit connection labels prior to executing execution strings.

### Verification Status
The local interface service was fully cycled, restoring normal packet transit and DNS resolution.

</details>

---

<details>
<summary><b>📥 Incident 2.0: Target ISO Download Obstruction (Windows Defender Mitigation)</b></summary>

### Root Cause Analysis
The deployment payload initialization failed initially because the host operating system's localized protection rules (Windows Defender/SmartScreen) flagged and interrupted the direct binary download from the main repository mirror.

### Remediation Protocol
To bypass the host inspection block, the retrieval mechanism was shifted from standard HTTP to a peer-to-peer distribution network, successfully pulling the verified system package via a torrent client.

> [!NOTE]
> If utilizing the qBittorrent pipeline for downloading security distribution assets, it is critical to activate a trusted VPN tunnel to mask peer traffic and secure host egress routing boundaries.

</details>

---

</details>

---

## 💡 Executive Competency & Core Takeaways

Through the deployment of this isolated infrastructure, I have developed the operational methodologies required to architect, provision, and audit secure sandboxed environments for cybersecurity practice. 

Expand the sections below to review the core technical breakthroughs mastered during this phase.

<details>
<summary><b>🌐 Concept 1.0: Network Boundary Isolation (NAT vs. NAT Network)</b></summary>

### Core Breakthrough
Mastered the structural differences between standard network address translation and a shared infrastructure segment. A unified `NAT Network` fabric was engineered to allow secure, multi-machine node communications within the laboratory without exposing the underlying host system.
* **Competency Focus:** <kbd>Isolated Subnet Architecture</kbd>

</details>

<details>
<summary><b>🔌 Concept 2.0: Software-Defined Virtual Networking Controls</b></summary>

### Core Breakthrough
Analyzed how hypervisor-level network adapters map traffic streams across hardware layers. This phase demonstrated how virtual adapter assignments directly govern host-to-guest boundaries and regulate communication paths between virtual instances.
* **Competency Focus:** <kbd>Hypervisor Fabric Engineering</kbd>

</details>

<details>
<summary><b>⚙️ Concept 3.0: Persistent Interface Provisioning (Static IP Allocations)</b></summary>

### Core Breakthrough
Developed hands-on experience in manually configuring and validating core network settings inside a Linux kernel. This involved architecting custom IPv4 scopes, binding persistent addresses, establishing default gateway endpoints, and routing traffic to recursive DNS resolvers.
* **Competency Focus:** <kbd>Static Network Management</kbd>

</details>

<details>
<summary><b>🛡️ Concept 4.0: System State Engineering & Platform Resilience</b></summary>

### Core Breakthrough
Evaluated the importance of establishing defensive baselines prior to launching risky or experimental payloads. Utilizing hypervisor snapshot mechanics provides a reliable, pristine recovery vector that acts as an uncorrupted foundation for future security labs.
* **Competency Focus:** <kbd>Immutable Rollback Vectors</kbd>

</details>

<details>
<summary><b>📝 Concept 5.0: Technical Reporting & Change Accountability</b></summary>

### Core Breakthrough
Recognized that comprehensive, structured logging is a critical operational asset in enterprise cybersecurity. Developing an administrative audit trail by capturing active configurations, documenting diagnostic commands, and recording error resolutions ensures full project transparency.
* **Competency Focus:** <kbd>Administrative Audit Logs</kbd>

</details>

---

## 🔐 Security & Ethical Use
This laboratory is intended strictly for education purposes only.

---

## 🔗 Tools & Resources
* 7-Zip: https://7-zip.org/download.html
* VirtualBox: https://virtualbox.org/wiki/Downloads
* Kali Linux: https://kali.org/get-kali

---

## 👤 Author
**Ayesha Irshad**
* Cybersecurity Professional **B084**
* Linkedin: https://www.linkedin.com/in/aisha-irshad-khan-26404743a/
---

## 📌 Project Information
Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub



