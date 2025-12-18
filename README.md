# Help-Desk-Administration-Lab

## 📌 Introduction

The **Help-Desk-Administration-Lab** is a hands-on learning project designed to simulate real-world help desk and IT administration tasks. This lab focuses on building practical skills that are essential for entry-level IT support, system administration, and service desk roles.

Through guided exercises and real scenarios, users will gain experience troubleshooting common issues, managing users, configuring systems, and understanding best practices used in professional IT environments.

---

## 📚 Table of Contents

1. [🧰 Tools and OS Requirements](#-tools-and-os-requirements)
2. [⚙️ Lab Setup Overview](#-lab-setup-overview)
3. [🖥️ Virtualization Setup](#-virtualization-setup)
4. [🐧 Linux Lab Setup](#-linux-lab-setup)
5. [🎫 Linux Tickets](#-linux-tickets)
6. [🪟 Windows Active Directory Setup](#-windows-active-directory-setup)
7. [🎫 Windows Tickets](#-windows-tickets)
8. [📚 Resources & Conclusion](#-resources-&-conclusion)
9. [🧠 Conclusion](#-conclusion)

## 🧰 Tools and OS Requirements

This lab is designed to simulate real-world help desk and IT administration environments. The following tools and operating systems are required to complete the labs successfully.

### 💻 Operating Systems
- **Two ISO Windows 11** (Client machines)
- **Windows Server 2019 or 2022 ISO** (Active Directory Domain Controller)
- **Linux (Ubuntu Server 20.04+) ISO**

### 🖥️ Virtualization
- **VirtualBox** or **VMware Workstation**
- Minimum **16 GB RAM** recommended
- At least **100 GB free disk space**

## ⚙️ Lab Setup Overview

This lab environment is designed to simulate a real-world help desk and IT administration workflow. It combines Windows, Linux, Active Directory, and a ticketing system to provide hands-on experience with common IT tasks.

### 🧪 Lab Architecture
- **Host Machine**: Windows 10/11 running virtualization software
- **Windows Server VM**: Acts as the Active Directory Domain Controller
- **Two Windows Clients VMs**: Joined to the domain for user and policy testing
- **Linux Server VM**: Used within the work environment to perform system administration tasks and run required supporting services such as SSH, scheduled update jobs, and user/group management.
- **Optional Security VM**: Kali Linux for troubleshooting and testing

### 🔗 Network Configuration
- **NAT Network** for internal lab communication between all virtual machines
- Provides **internet access** for updates and package installations
- **DNS configured through the Domain Controller** to support Active Directory services

### 🎯 Lab Objectives 
- Practice Active Directory user and group management
- Apply Group Policy Objects (GPOs)
- Troubleshoot common help desk issues
- Manage tickets and document resolutions
- Gain experience with Linux server administration

## 🖥️ Virtualization Setup
### **VirtualBox**
<img width="632" height="251" alt="Screenshot 2025-10-12 130317" src="https://github.com/user-attachments/assets/bb6e4789-e00c-477c-aa14-1951266cb0b9" />
<img width="1902" height="837" alt="Screenshot 2025-10-12 130345" src="https://github.com/user-attachments/assets/248636d7-a7c2-4802-a233-05fb8d1ed754" />
Download the latest VirtualBox from https://www.virtualbox.org/

YouTube Tutorial: https://www.virtualbox.org/wiki/Downloads

Here is a video of how you add virtual machines to VirtualBox: https://www.youtube.com/watch?v=CMGa6DsGIpc&t=25s&pp=ygUXdmlydHVhbGJveCBhZGQgbWFjaGluZXM%3D

## 🐧 Linux Lab Setup
<img width="660" height="359" alt="image" src="https://github.com/user-attachments/assets/721b94bb-781a-4c9b-87f2-25b7b179090e" />


1. Download **Ubuntu Desktop 22.04 LTS** ISO.
2. Create a new virtual machine in VirtualBox / VMware.
3. Assign resources:
   - 2 CPU cores
   - 4 GB RAM
   - 40 GB storage
4. Set network adapter to **NAT Network**.
5. Boot the VM using the Ubuntu Desktop ISO.
6. Select **Install Ubuntu**.
7. The rest of the installation depends on you; if you have any experience with Ubuntu, if not, then watch this video: https://www.youtube.com/watch?v=Hva8lsV2nTk&list=PLLcQLz3ZRgqLKS59bF78fsPU0y-3kKxCb&index=9

## 🔄 Update and Upgrade System

After reaching the Ubuntu desktop, open **Terminal** and run:

```bash
sudo apt update && sudo apt upgrade -y
```

## Install and Enable SSH

Installing SSH allows remote administration of the Linux system.

1. Install OpenSSH Server
```
sudo apt install openssh-server -y
```

2. Verify SSH Service Status
```
sudo systemctl status ssh
```

3. If not running, start and enable it:
```
sudo systemctl enable ssh
sudo systemctl start ssh
```

## 👥 User and Group Setup (Lab Requirement)

To simulate a real-world Linux administration environment, lab users must create **at least three local users** and **one group**.

### 👤 User Accounts
Create the following local users:

- **alex.it** — IT Support user (standard access)
- **jamie.support** — Help Desk user (standard access)
- **taylor.user** — End user (standard access)

> ⚠️ **Important:**  
> Do **not** grant sudo privileges to these users unless explicitly instructed.

---

### 👥 Group
Create the following group:

- **helpdesk**

Add the appropriate users to this group as required by the tickets below.

---

### 📸 Snapshot Best Practices

> **Important:** Take snapshots **before and after major configuration steps**. Snapshots allow you to quickly roll back if something breaks.

**How to take a snapshot in VirtualBox:**
1. **VirtualBox Manager** → Select VM → `Snapshots` → `Take`
2. Name the snapshot clearly (examples below)
3. Click **OK**

---

## 🎫 Linux Tickets

The following practice tickets are designed to simulate **real-world IT Help Desk scenarios**.  
Each ticket includes a problem description, but **does not include a solution**, allowing students to troubleshoot, document findings, and resolve issues on their own.

Before you practice: Please take your time to work through these tickets **before doing any research**.  
These tickets are designed to help you practice **critical thinking, troubleshooting, and documentation skills** by encouraging you to analyze each issue using your existing knowledge and logical reasoning.

---

### 🎫 Ticket 1: Create User Account
- **Client:** IT Manager  
- **Issue Type:** User Management  
- **Priority:** Low  

**Description:**  
Create a new local user named `jamie.support`.  
Ensure the account can log in and does **not** have administrative (sudo) privileges.

---

### 🎫 Ticket 2: Modify Group Membership
- **Client:** Help Desk Supervisor  
- **Issue Type:** Access Management  
- **Priority:** Medium  

**Description:**  
Add `alex.it` and `jamie.support` to the `helpdesk` group.  
Confirm that `taylor.user` is **not** a member of this group.

---

### 🎫 Ticket 3: Remove Unnecessary Privileges
- **Client:** Security Team  
- **Issue Type:** Privilege Review  
- **Priority:** Medium  

**Description:**  
Audit all local users and ensure that **only authorized accounts** have sudo access.  
Remove sudo privileges from any user accounts that should be standard users.

## 🪟 Windows Active Directory Setup

This section covers setting up **Windows Active Directory (AD)** in a VirtualBox lab environment, including best practices like snapshots to protect your work.

---

## 📥 Downloading Windows ISOs

### 🔹 Windows Server (2019 or 2022)
<img width="1000" height="750" alt="image" src="https://github.com/user-attachments/assets/14c830e4-0cc5-4ce1-aab1-b215762a368a" />

1. Visit the **Microsoft Evaluation Center**: https://www.microsoft.com/en-us/evalcenter
2. Download **one** of the following:
   - **Windows Server 2019**
   - **Windows Server 2022**
3. Select the **ISO** format
4. Save the file locally

> ✅ The evaluation version is fully functional and ideal for lab environments.

---

### 🔹 Windows 11 (Desktop Clients)
<img width="724" height="407" alt="image" src="https://github.com/user-attachments/assets/e9a680b3-e7b8-4af0-9aaf-494604498b87" />

1. Visit the **Microsoft Evaluation Center**: https://www.microsoft.com/en-us/evalcenter
2. Download:
   - **Windows 11 Enterprise ISO**
3. Save the ISO locally

> ℹ️ **Only one Windows 11 ISO is required**  
> The same ISO will be used to install **multiple Windows 11 desktop VMs**

> ⚠️ **Windows 11 Pro or Enterprise is required** for domain joining  
> (Home edition will NOT work)

---

## 🖥️ Installing Windows Server (Domain Controller – DC01)

### 1️⃣ Create the Virtual Machine
- Open **VirtualBox**
- Click **New**
- Configure the VM:
  - **Name**: `DC01`
  - **Type**: Microsoft Windows
  - **Version**: Windows Server 2019 / 2022 (64-bit)
  - **RAM**: 4–8 GB
  - **CPU**: 2 cores (or more)
  - **Disk**: 50 GB (VDI, Dynamically Allocated)

Attach the **Windows Server ISO** to the VM.

---

### 2️⃣ Install the Operating System
1. Start the `DC01` VM
2. Click **Install Now**
3. Select:
   - **Windows Server (Desktop Experience)**
4. Choose **Custom: Install Windows only**
5. Select the empty disk and click **Install**
6. Wait for the installation to complete

Set the **Administrator password** when prompted.

#### 🧩 Installing Active Directory Domain Services (AD DS)

1. Open **Server Manager**
2. Click **Add roles and features**
3. Select **Role-based or feature-based installation**
4. Select the local server (`DC01`)
5. Install:
   - ☑ Active Directory Domain Services
   - ☑ DNS Server
6. Click **Install**

---

#### Promote Server to Domain Controller

1. In **Server Manager**, click the notification flag
2. Select **Promote this server to a domain controller**
3. Choose:
   - **Add a new forest**
4. Domain name:
5. Set DSRM password
6. Complete the wizard and reboot
7. After reboot, the server is now the Domain Controller.

---

#### 🔐 Installing Active Directory Certificate Services (AD CS)

This section covers the installation and configuration of **Active Directory Certificate Services (AD CS)** on a Windows Server Domain Controller.

> **Active Directory Certificate Services (AD CS)** allows an organization to create, manage, and distribute digital certificates. These certificates are used to secure communications, authenticate users and devices, and ensure data integrity within a network.

---

#### 📦 Install AD CS Role

1. Open **Server Manager** (opens automatically by default)
2. Click **Manage → Add Roles and Features**
3. Click **Next** on the *Before You Begin* page
4. On the **Installation Type** page, select:
   - **Role-based or feature-based installation**
5. Click **Next**
6. Select your **local server** from the server pool → Click **Next**
7. On the **Server Roles** page, check:
   - **Active Directory Certificate Services**
8. When prompted, click **Add Features**
9. Click **Next** through the **Features** page (leave defaults)
10. Continue clicking **Next** until you reach the **Confirmation** page
11. Check:
    - **Restart the server automatically if required**
12. Click **Install**

---

#### ⚙️ Configure Active Directory Certificate Services (AD CS)

1. In **Server Manager**, click the **flag icon** (top-right)
2. Select **Configure Active Directory Certificate Services on the destination server**
3. Leave the default credentials selected → Click **Next**
4. On the **Role Services** page, select:
   - **Certification Authority**
5. Click **Next**
6. Choose:
   - **Enterprise CA** (integrates with Active Directory)
7. Click **Next**
8. Select:
   - **Root CA** (first CA in the environment)
9. Click **Next**
10. Select:
    - **Create a new private key**
11. Click **Next**
12. Leave the **Cryptography** settings and **CA Name** as default
13. Leave the **Validity Period** set to **5 years**
14. Leave all remaining settings as default
15. Click **Configure**

---

## 🖥️ Installing Windows 11 Client Desktops

We will install **two Windows 11 desktop VMs** that will later be joined to the Active Directory domain.

- **Client 1**: `WIN11-CLIENT01`
- **Client 2**: `WIN11-CLIENT02`

> ℹ️ The **same Windows 11 Enterprise ISO** will be used for both machines.

---

### 1️⃣ Create the First Windows 11 VM (CLIENT01)

1. Open **VirtualBox**
2. Click **New**
3. Configure the VM:
   - **Name**: `WIN11-CLIENT01`
   - **Type**: Microsoft Windows
   - **Version**: Windows 11 (64-bit)
   - **RAM**: 4 GB (8 GB recommended)
   - **CPU**: 2 cores
   - **Disk**: 50 GB (VDI, Dynamically Allocated)

4. Attach the **Windows 11 Enterprise ISO**

---

### 2️⃣ Install Windows 11 (CLIENT01)

1. Start the VM
2. Click **Install Now**
3. When prompted for a product key:
   - Select **I don’t have a product key**
4. Choose:
   - **Windows 11 Enterprise**
5. Accept the license agreement
6. Select:
   - **Custom: Install Windows only**
7. Select the empty disk → Click **Next**
8. Wait for the installation to complete

---

### 3️⃣ Windows Setup 

1. Select your **Region** and **Keyboard layout**
2. Skip additional keyboard layouts if prompted
3. When asked to connect to a network:
   - Select **I don’t have internet**
   - Choose **Continue with limited setup**
4. Create a **local account**:
   - Username
   - Password
5. Disable optional privacy settings (recommended for lab use)
6. Complete setup and reach the desktop

---

### 📸 Snapshot: Clean Client Install
> **Take a snapshot after reaching the desktop**

**Snapshot Name:**  
`WIN11-CLIENT01 - Clean Install`

This snapshot allows you to roll back before domain joining or software installation.

---

### 4️⃣ Install VirtualBox Guest Additions
<img width="499" height="388" alt="image" src="https://github.com/user-attachments/assets/18825703-64c3-4aa3-a7a5-57c72a93e445" />

1. From the VM menu:
   - `Devices → Insert Guest Additions CD Image`
2. Open **File Explorer**
3. Run:
   - `VBoxWindowsAdditions.exe`
4. Follow the installer prompts
5. Reboot the VM when prompted

📸 **Snapshot Recommended:**  
`WIN11-CLIENT01 - Guest Additions Installed`

---

### 5️⃣ Create the Second Windows 11 VM (CLIENT02)

Repeat **Steps 1–4** using the following changes:

- **VM Name**: `WIN11-CLIENT02`
- Use the **same Windows 11 Enterprise ISO**
- Use the same network settings (**NAT Network**)

📸 **Snapshot Name:**  
`WIN11-CLIENT02 - Clean Install`

### 📸 Snapshot Best Practices

> **Important:** Take snapshots **before and after major configuration steps**. Snapshots allow you to quickly roll back if something breaks.

**How to take a snapshot in VirtualBox:**
1. **VirtualBox Manager** → Select VM → `Snapshots` → `Take`
2. Name the snapshot clearly (examples below)
3. Click **OK**

# 🪟 Windows Server: Setup Users, OUs, and Groups

This section focuses on configuring **Active Directory Users, Organizational Units (OUs), and Security Groups** on the Domain Controller. These components form the foundation of centralized identity management, access control, and policy enforcement in a Windows domain environment.

---

## 👥 Creating Domain Users

Domain users are centrally managed accounts that allow users to log in to any domain-joined machine using the same credentials.

### Open Active Directory Users and Computers (ADUC)
- Press **Windows + R**, type `dsa.msc`, press **Enter**
- Or open **Server Manager → Tools → Active Directory Users and Computers**

---

### Create Domain Users
1. Expand your domain (e.g., `mydomain.local`)
2. Right-click **Users** → **New → User**
3. Enter user details:
   - First name
   - Last name
   - User logon name (e.g., `jdoe@mydomain.local`)
   - Name at least two users Jane Doe and John Smith to make things easier for practing tickets
4. Create **three users** for this lab
5. Set the password:
   - Check **Password never expires** (lab environment only)
6. Finish the wizard

✅ These accounts are now managed centrally through Active Directory.

---

## 🖥️ Joining Windows 11 Clients to the Domain

Clients must be domain-joined before domain authentication and access control will function.

Before joining the domain, the client must use the **Domain Controller as its DNS server**. Active Directory authentication depends on DNS, and domain joins will fail if public DNS servers are used.

### Set DNS on Windows 11 Client

1. Open **Settings**
2. Go to **Network & Internet**
3. Select your active network adapter (Ethernet or Wi-Fi)
4. Click **Edit DNS settings**
5. Change DNS settings to **Manual**
6. Enable **IPv4**
7. Configure:
   - **Preferred DNS**: *Domain Controller IP*  
8. Leave **Alternate DNS** empty
9. Click **Save**

⚠️ **Do not use public DNS servers** such as `8.8.8.8` or `1.1.1.1`

---

#### Verify DNS Configuration

Open **Command Prompt** and run:

```cmd
ipconfig /all
```

### Join the Domain

1. Open **Settings**
2. Go to **System → About**
3. Select **Domain or workgroup**
4. Click **Join a domain**
5. Enter The domain name(mydomain.local):

## 🗂️ Organizational Units (OUs)

Organizational Units help organize users and computers while allowing targeted Group Policy application and delegated administration.

### Benefits of OUs
- Logical organization (by department or role)
- Scoped Group Policy application
- Delegated administrative control

---

### Create Organizational Units
1. In ADUC, right-click your domain
2. Select **New → Organizational Unit**
3. Create the following OUs:
   - `IT`
   - `Management`
   - `Engineering`
4. Click **OK** for each

---

### Assign Users to OUs
1. Open the **Users** container
2. Drag and drop each user into their respective OU:
   - IT users → `IT`
   - Managers → `Management`
   - Engineers → `Engineering`

---

### Create a Sub-OU (IT Department)
1. Right-click the `IT` OU → **New → Organizational Unit**
2. Name it:
   - `Support_Team` or `IT_Administrators`
3. Click **OK**

This allows more granular policy and permission control within IT.

---

## 👥 Security Groups

Security Groups are used to assign permissions to resources such as shared folders, printers, and applications.

### Group Types
- **Security Groups**: Used for access control
- **Distribution Groups**: Used only for email (not used in this lab)

---

### Create a Security Group (Engineering)
1. Right-click the `Engineering` OU → **New → Group**
2. Configure:
   - **Group Name**: `EngineeringShare`
   - **Group Scope**: Global
   - **Group Type**: Security
3. Click **OK**

---

### Add Members to the Group
1. Right-click `EngineeringShare` → **Properties**
2. Open the **Members** tab
3. Click **Add**
4. Select Engineering users
5. Click **OK**

All members now inherit permissions assigned to this group.

---

## 📁 Shared Folder Configuration (Engineering)

Shared folders allow controlled access to resources using group-based permissions.

### Create a Shared Folder
1. Open **Server Manager**
2. Navigate to **File and Storage Services → Shares**
3. Click **Tasks → New Share**
4. Select **SMB Share – Quick**
5. Choose location (default `C:\`)
6. Name the share:
   - `EngineeringShare`

---

### Configure Permissions
1. Choose **Customize permissions**
2. Disable inheritance → Convert inherited permissions
3. Remove unnecessary users (e.g., Everyone)
4. Add the **EngineeringShare** group
5. Assign permissions:
   - Read & execute
   - List folder contents
   - Read
   - Write
6. Finish the wizard

---

### Verify Access
- Log in from a domain-joined Windows 11 client
- Open:  
  `\\ServerName\EngineeringShare`
- Confirm access works only for Engineering users

---

## 🗺️ Mapping the Network Drive
1. On the client machine, open **File Explorer**
2. Right-click **This PC** → **Map network drive**
3. Choose a drive letter (e.g., `E:`)
4. Enter the path:

## 🎫 Windows Tickets

The following practice tickets are designed to simulate **real-world IT Help Desk scenarios**.  
Each ticket includes a problem description but **does not include a solution**, allowing students to troubleshoot, document findings, and resolve issues on their own.

Before you practice: Please take your time to work through these tickets **before doing any research**.  
These tickets are designed to help you practice **critical thinking, troubleshooting, and documentation skills** by encouraging you to analyze each issue using your existing knowledge and logical reasoning.

---

### 🎫 Ticket 1: Password Reset Request
- **Client:** Jane Doe
- **Issue Type:** Account Access
- **Priority:** Medium
- **Description:** User forgot their password and is unable to log in.

---

### 🎫 Ticket 2: Unlock Locked Domain Account
- **Client:** John Smith
- **Issue Type:** Account Access
- **Priority:** High
- **Description:** User reports their domain account is locked after multiple failed login attempts.

---

### 🎫 Ticket 3: Add User to Security Group
- **Client:** Engineering Manager
- **Issue Type:** Access Control
- **Priority:** Medium
- **Description:** Request to add a newly created domain user to the **EngineeringShare** security group.

**User Information**
- **First Name:** Jim
- **Last Name:** William
- **Department:** Engineering

---

### 🎫 Ticket 4: Disable Changing Background
- **Client:** Engineering Department
- **Issue Type:** Account Management
- **Priority:** High
- **Description:** Request to disable Engineering department users ability to change background.

---

### 🎫 Ticket 5: Create New Domain User Account
- **Client:** IT Department
- **Issue Type:** Account Management
- **Priority:** Medium
- **Description:** Request to create a new domain user account for a newly hired employee.

## 📚 Resources & Conclusion

### 🔗 Learning Resources

If you would like to continue building your skills beyond this lab, the following resources are highly recommended:

- **TCM Security (The Cyber Mentor)**  
  Hands-on cybersecurity training covering Linux, Windows, Active Directory, and real-world attack/defense concepts.  
  https://certifications.tcm-sec.com

- **TryHackMe**  
  Beginner-to-intermediate labs for Linux administration, Windows environments, and security fundamentals.  
  https://tryhackme.com

- **Hack The Box (Academy)**  
  In-depth technical training focused on system administration, Active Directory, and security operations.  
  https://academy.hackthebox.com

- **Linux Foundation Training**  
  Official Linux system administration and certification prep courses.  
  https://training.linuxfoundation.org

- **Microsoft Learn**  
  Free, official learning paths for Windows Server, Active Directory, and enterprise administration.  
  https://learn.microsoft.com

---

### 🧠 Conclusion

After taking the **TCM Practical Help Desk Analyst (PHDA) exam**, I was inspired to build this lab as a way to reinforce my own skills while also helping others gain **hands-on, real-world experience**.

This lab is designed to simulate realistic IT Help Desk and junior system administration tasks across both **Linux and Windows Active Directory environments**. Rather than providing step-by-step solutions, the focus is on **critical thinking, troubleshooting, and documentation**, which are essential skills for anyone entering IT or cybersecurity roles.

My goal is for this lab to serve as a practical learning environment where users can confidently practice, make mistakes, and grow their technical abilities in a safe, controlled setting.
