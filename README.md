# Active-Directory-IAM-Lab-Group-Based-Access-Control-with-Shared-Folders

🛡️ Active Directory IAM Lab: Group-Based Access Control with Shared Folders
📅 Date Completed: May 13, 2025
This lab demonstrates a full Active Directory IAM scenario involving user and group management, DNS resolution, and access control through a shared folder using NTFS and share permissions — all within a VirtualBox lab setup.

🛠️ Tools & Environment
Virtualization: Oracle VirtualBox

Operating Systems:

Windows Server 2019 (Domain Controller)

Windows 10 (Client Machine)

Key Services:

Active Directory Domain Services

DNS

File and Printer Sharing

🔧 Step-by-Step Instructions
🖥️ Step 1: Create Virtual Machines & Network
Created two VMs: DC01 (Server) and Win10 (Client).

Attached both to Host-Only Adapter.

📸 ![image](https://github.com/user-attachments/assets/adc22a9a-4812-4049-b967-b098d0fe8358)


📸 ![image](https://github.com/user-attachments/assets/f17ccffd-0b99-4f06-b224-bcb9b69a5bad)


🌐 Step 2: Assign Static IPs
DC01:

IP: 192.168.xx.xx

Subnet: 255.255.255.0

Win10:

IP: 192.168.xx.xx

DNS: 192.168.xx.xx

📸 ![image](https://github.com/user-attachments/assets/1ad515cc-4895-4236-bd8a-7745b2f7317c)

📸 ![image](https://github.com/user-attachments/assets/f338a2d7-6294-4705-b618-9e73b0cf8bac)


🧠 Step 3: Configure DC01
Promoted Server to Domain Controller: lab.local

Installed DNS Server role

Created OU: IAM-Users

Created users: ssmith, alica.jordan

Created group: HR-Team

📸![image](https://github.com/user-attachments/assets/248221b5-8906-4a11-a0e5-bf7e40781364)
📸![image](https://github.com/user-attachments/assets/4e958ae2-d38a-4765-bb5c-f7571d07558a)
📸![image](https://github.com/user-attachments/assets/e4bec9c2-3c9b-4b06-8516-9501a6322cf0)


🧑‍💻 Step 4: Join Windows 10 VM to Domain
Joined domain: lab.local

Restarted VM

Logged in as: LAB\\ssmith

📸 ![image](https://github.com/user-attachments/assets/982f7f5b-7c1c-49ec-90fa-6a67d8210eef)

📸 ![image](https://github.com/user-attachments/assets/5cb670c4-f95c-4c26-b50a-b8362963e51f)

📸 ![image](https://github.com/user-attachments/assets/18d2c3db-b864-4c26-8065-963d1c35b439)


🖱️ Step 5: DNS Testing
Verified DC was pingable using IP and hostname

Ran nslookup lab.local to ensure proper DNS resolution

Cleared and re-tested after updating DNS on the client

📸 ![image](https://github.com/user-attachments/assets/90a12282-f260-48ca-b5de-8c70a4a28718)


🔒 Step 6: Create & Share Folder (HR-Docs)
On DC01, created folder: C:\HR-Docs

Right-click → Properties → Sharing → Advanced Sharing → Shared as HR-Docs

Set share permissions to allow HR-Team Full Control

📸 ![image](https://github.com/user-attachments/assets/c63c979c-669f-4d50-816a-ed9ff79cc8ae)




🛡️ Step 7: NTFS Permissions
Security tab → Added HR-Team with Modify and Read rights

Disabled inherited permissions and removed Users

📸 ![image](https://github.com/user-attachments/assets/28a96a38-db00-4776-9ade-e904eeb668e8)

🔗 Step 8: Enable Sharing on Windows 10
Turned on:

Network Discovery

File and Printer Sharing

Public Folder Sharing

📸 ![image](https://github.com/user-attachments/assets/6e6ae5ed-0037-4fb4-99f1-7d6e16e542c8)


🧪 Step 9: Access Validation
Logged in as jsmith on the client

Navigated to: \\DC01\HR-Docs

Initially saw permission denied

Adjusted permissions again on DC01 (both Share and NTFS) to grant HR-Team full access

Final attempt: successful access to folder contents

📸 ![image](https://github.com/user-attachments/assets/02c26aa8-d1c8-4ecf-a2f4-2d19d8360718)

📸 ![image](https://github.com/user-attachments/assets/a8a88929-d601-4665-9a19-29fde17d57a3)


✅ Final Outcome
I demonstrated:

Domain joining from a client machine

DNS name resolution

Group-based folder permission management

File sharing across the domain

Troubleshooting and resolving access issues
