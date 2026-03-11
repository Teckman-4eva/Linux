# 🐧 Linux-Labs: Ubuntu & Termux SSH Setup

This repository documents the process of establishing a secure SSH connection between an Android device (via **Termux**) and an Ubuntu instance running in **VirtualBox**. It specifically addresses the common "Connection Timeout" issues caused by virtualized network stacks.

---

## 🛠️ 1. Project Overview
The goal of this project is to enable remote command-line access to a virtualized Linux environment from a mobile device using standard OpenSSH tools.

### Prerequisites
* **Host PC:** Running Oracle VM VirtualBox.
* **Guest OS:** Ubuntu (Server or Desktop).
* **Mobile Client:** Android device with [Termux](https://play.google.com/store/apps/details?id=com.termux) installed.
* **Network:** Both devices must be on the same local Wi-Fi/LAN.

---

## 🚀 2. Step-by-Step Configuration

### Step A: VirtualBox Network Fix
By default, VirtualBox uses **NAT**, which places the VM behind a private firewall that is unreachable from external devices.
1. Power off the Ubuntu VM.
2. Navigate to **Settings > Network**.
3. Change **Attached to:** from `NAT` to `Bridged Adapter`.
4. Select your PC's active network interface (e.g., your Wi-Fi card).



### Step B: Ubuntu Server Setup
Open your Ubuntu terminal and verify the SSH service:

bash
Check if SSH is active

sudo systemctl status ssh

# If not installed, run:
sudo apt update && sudo apt install openssh-server -y

# Find your Local IP Address
ip --brief addr

Open Termux on your Android phone and prepare the client:

# Update packages and install SSH tools
pkg update && pkg upgrade
pkg install openssh

# Connect to the Ubuntu machine
ssh <username>@<ubuntu-ip-address>

Verify and testing 

# Create and verify a test file
touch File1
echo "We are logged in from device" > File1
cat File1

<img width="1062" height="685" alt="ORACLE VBOX" src="https://github.com/user-attachments/assets/a52c05c0-3eb4-44a6-bca1-bcb4c4d429c6" />

<img width="1909" height="1079" alt="ubuntu" src="https://github.com/user-attachments/assets/f53c77f7-4dd7-4a5b-9c48-9e3099ba4382" />

![Termux](https://github.com/user-attachments/assets/ce9c2483-0aad-42e1-b487-1c910d42d2b1)


