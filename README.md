#  🔐  NETWORKWALKSEMMANUEL-B083-WK1-PM1-CYBERSECURITY-LAB-SETUP
 # 📌 Project Overview
This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.
 # 🎯 Objectives
The main objectives of this project are to:

Install and configure VirtualBox.
Install/import Kali Linux as a virtual machine.
Create a private NAT Network for the cybersecurity lab.
Configure network connectivity for Kali Linux.
Assign a consistent IP address to the Kali VM.
Verify network connectivity and DNS resolution.
Take a clean VM snapshot for recovery.
Document the complete setup process.
Prepare the environment for future cybersecurity projects.
# 🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

Network reconnaissance
Port scanning
Vulnerability assessment
Packet analysis
Web security testing
Exploitation practice
Security-tool experimentation
⚠️ Important: This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.
# 🏗️ Lab Architecture
#<img width="700" height="500" alt="download" src="https://github.com/user-attachments/assets/dbc60b5a-0143-45dd-8454-9141cb60e3ea" />

 ## 🖥️ Lab Configuration

| Component | Configuration |
|:---|:---|
| 🖥️ Host OS | Windows 10 |
| 🧠 Host RAM | 8 GB |
| ⚡ Processor | Intel Core i7 |
| 🧰 Hypervisor | VirtualBox 7.2 |
| 🐉 Security OS | Kali Linux 2026.2 |
| 🧠 Kali RAM | 2048 MB |
| 🌐 Virtual Network | NAT Network |
| 🌐 Network Address | 10.0.0.0/24 |
| 🔐 Kali IP Address | 10.0.0.2/24 |
| 🚪 Default Gateway | 10.0.0.1 |
| 🌍 DNS Server | 8.8.8.8 |
| 💻 Future VM Range | 10.0.0.3–10.0.0.99 |
# 🛠️ Lab Setup Procedure



---

## Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip

---

## Step 2. Install VirtualBox

VirtualBox was installed as the hypervisor.

---

## Step 3. Create the NAT Network

A dedicated NAT Network was created in VirtualBox.

**Configuration:** Network Name: NatNetwork IPv4 Prefix: 10.0.0.0/24 DHCP: Enabled IPv6: Disabled

<img width="1362" height="724" alt="image" src="https://github.com/user-attachments/assets/2c14a764-1a05-4ecd-8d5c-697d75bd5a3c" />
A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab
## Step 4. Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

```text
Adapter 1
Attached to: NAT Network
Network: NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
```

The VM was allocated:

```text
RAM: 2048 MB
```
<img width="1366" height="662" alt="image" src="https://github.com/user-attachments/assets/506b0bde-48fc-4ec7-8488-14a49a805288" />
A shared folder was also configured for transferring required files between the host operating system and the Kali VM.
##  Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```text
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.
<img width="1366" height="662" alt="image" src="https://github.com/user-attachments/assets/392deb45-25a9-42b6-a9d0-ea26b7f235d4" />
# 🔎 Lab Verification

| ❇️ Test | 🧾 Command | 🎯 Expected Result |
| --- | --- | --- |
| 🌐 Check IP address | `ip a` | Correct Kali IP displayed |
| 📡 Test gateway | `ping 10.0.0.1` | Successful replies |
| 🌍 Test Internet connectivity | `ping 8.8.8.8` | Successful replies |
| 🔎 Test DNS resolution | `nslookup networkwalks.com` | Domain resolves |
| 🧰 Verify Nmap | `nmap --version` | Nmap version displayed |
| 🔄 Verify snapshot | Restore snapshot and run `ip a` | Baseline configuration restored |

## Example Results

```text
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8
```


### 1. Download Required Tools

- VirtualBox: https://www.virtualbox.org/
- Kali Linux: https://www.kali.org/get-kali/
- 7-Zip: https://www.7-zip.org/

### 2. Virtual Machine Configuration

1. Install Oracle VirtualBox.
2. Download Kali Linux ISO.
3. Create a new virtual machine.
4. Select Linux and Debian 64-bit.
5. Allocate RAM and CPU resources.
6. Create a virtual hard disk.
7. Attach Kali Linux ISO.
8. Install Kali Linux.

### 3. Network Configuration

Open:

VirtualBox → Settings → Network → Adapter 1

Select NAT or NAT Network according to lab requirements.

### 4. Network Verification

Run these commands in Kali Linux:

```bash
ip addr
ip route
nmcli device status
ping -c 4 1.1.1.1
getent hosts kali.org
```

### 5. Static IP Configuration

First identify the network connection:

```bash
nmcli connection show
```

Configure a static IP using your actual lab network details:

```bash
sudo nmcli connection modify "<CONNECTION_NAME>" ipv4.method manual ipv4.addresses "<IP_ADDRESS>/<PREFIX>" ipv4.gateway "<GATEWAY_IP>" ipv4.dns "<DNS_IP>"
```

Activate the connection:

```bash
sudo nmcli connection up "<CONNECTION_NAME>"
```

### 6. Troubleshooting

Common issues:

- Network connectivity problems
- Incorrect IP configuration
- DNS resolution errors
- VirtualBox VT-x errors
- Virtual machine startup problems

### 7. Snapshot Creation

After successfully configuring Kali Linux:

1. Open VirtualBox.
2. Select the Kali VM.
3. Open Snapshots.
4. Create a snapshot.

Snapshot name:

Clean Kali - Network Setup

## What I Learned

1. Difference between NAT and NAT Network.
2. Virtual machine network configuration.
3. Static IP configuration.
4. Linux network troubleshooting.
5. Virtual machine snapshot management.
6. Basic cybersecurity lab preparation.

## Author

Muskan Zaheer

Cybersecurity Internship  
Networkwalks

## Ethical Disclaimer

This laboratory is intended for educational purposes. Perform security testing only on systems you own or have explicit permission to test.






## 🌐 Socials:
[![Discord](https://img.shields.io/badge/Discord-%237289DA.svg?logo=discord&logoColor=white)](https://discord.gg/muskandevops) [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/https://www.linkedin.com/in/muskan-zaheer-165b89433) [![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://youtube.com/@www.youtube.com/@LearnenglishwithMuskanAndPihu) 

# 💻 Tech Stack:
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)
# 📊 GitHub Stats:
![](https://github-readme-stats.shion.dev/api?username=Muskan-cyber-hub&theme=dark&hide_border=false&include_all_commits=true&count_private=true)<br/>
![](https://streak-stats.demolab.com/?user=Muskan-cyber-hub&theme=dark&hide_border=false)<br/>
![](https://github-readme-stats.shion.dev/api/top-langs/?username=Muskan-cyber-hub&theme=dark&hide_border=false&include_all_commits=true&count_private=true&layout=compact)

## 🏆 GitHub Trophies
![](https://github-profile-trophy.vercel.app/?username=Muskan-cyber-hub&theme=radical&no-frame=false&no-bg=true&margin-w=4)

---
[![](https://komarev.com/ghpvc/?username=Muskan-cyber-hub&icon=0&color=0)](https://visitcount.itsvg.in)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) --> 
