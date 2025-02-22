<p align="center">
<img width="542" alt="Screen Shot 2025-02-22 at 10 40 06 AM" src="https://github.com/user-attachments/assets/a1e0d5ec-dfb2-4359-9bdc-da4f4b2c22b2" />

<h1> Active Directory Deployment </h1>

<h2> Description </h2>
Deploying Active Directory (AD) is essential for managing users, devices, and security within an organization. It organizes and controls access to company resources, making it easier to manage permissions and security policies. In this lab, we will set up AD, create users, and practice logging in with users that will be created! 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2) Macbook
- Windows Server 2022

<h2>Installation Steps </h2>

- Install the Active Directory Domain Services
- Promote the Server to a Domain Controller
- Verify Active Directory Deployment
- Join a Computer to the Domain

<h2> Walkthrough </h2>
Create a Domain Controller Virtual Machine (VM) in Azure using Windows Server 2022. For this project, we will refer to ours as DC-1. Then, create a Windows 10 client VM (ours will be named Client-1). Make sure it is within the same Resource Group and Virtual Network (VNet)
<p>


<img width="501" alt="Screen Shot 2025-02-22 at 1 23 21 AM" src="https://github.com/user-attachments/assets/afeca078-4e95-4629-813f-65747fae2f19" />

Login to and install Active Directory Domain Services:
</p>
<img width="383" alt="Screen Shot 2025-02-21 at 9 26 34 AM" src="https://github.com/user-attachments/assets/7a97567c-c471-4b71-b104-5bc45118d428" />

<p>
Setup a new forest as your prefered name. It can be anything and install it. Ex: mydomain.com 
</p>
<img width="456" alt="Screen Shot 2025-02-20 at 11 44 22 PM" src="https://github.com/user-attachments/assets/f797d12a-3311-4680-b6a1-496254286a5e" />


Restart and then log back into DC-1 as user: x.com\xuser name:
</p>
<img width="658" alt="Screen Shot 2025-02-21 at 9 04 50 AM" src="https://github.com/user-attachments/assets/7b8cf3c7-e0c0-49f0-b11e-6bfab0a855ee" />

Create a Domain Admin user within the domain. In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES” and create a new user named “_ADMINS”:
</p>
<img width="445" alt="Screen Shot 2025-02-20 at 11 45 19 PM" src="https://github.com/user-attachments/assets/94d03687-6fb7-40e1-b886-762d2bf38bf4" />


Create a new employee: 
</p>

<img width="504" alt="Screen Shot 2025-02-20 at 11 45 48 PM" src="https://github.com/user-attachments/assets/924041b4-a386-4b7d-bbe9-7c9723895cc0" />


<p>
Add to the “Domain Admins” Security Group. Log out / close the connection to and log back in: 
</p>
<img width="506" alt="Screen Shot 2025-02-20 at 11 46 42 PM" src="https://github.com/user-attachments/assets/5a26dce2-4256-4432-bf50-1337ffa23ec8" />

Login as the original local admin and join it to the domain (computer will restart):
</p>
<img width="509" alt="Screen Shot 2025-02-20 at 11 46 26 PM" src="https://github.com/user-attachments/assets/e229607d-96a7-45c4-a618-40add0f06335" />

<p>
Login to the Domain Controller and verify user shows up in ADUC:
</p>
<img width="486" alt="Screen Shot 2025-02-20 at 11 42 27 PM" src="https://github.com/user-attachments/assets/d28381db-e019-43b0-911f-1a8d2f08056b" />

<p>
Create a new OU named “_CLIENTS” and drag Client-1 into there:
</p>
<img width="485" alt="Screen Shot 2025-02-20 at 11 42 14 PM" src="https://github.com/user-attachments/assets/29efc97d-fdd7-43f4-8853-f41fdff22f12" />

<p>
Log into user desktop as x.com\xuser name. Then, open system properties. Click “Remote Desktop” and allow “domain users” access to remote desktop:
</p>

<img width="557" alt="Screen Shot 2025-02-20 at 11 40 51 PM" src="https://github.com/user-attachments/assets/8a6f5936-5cf8-4b5d-a0c5-637fdefa34a1" />

<h2> Add Users </h2> 
  
<p>
Login to DC-1 as admin created. Open PowerShell as an administrator. Create a new File and paste the contents of the script into it (https://github.com/Xinloiazn/configure-ad/blob/main/adscript.ps1). Lastly, you will see additional users: 
</p>

<img width="430" alt="Screen Shot 2025-02-20 at 11 40 20 PM" src="https://github.com/user-attachments/assets/54a32d30-a511-42d1-807a-7a6d419000cd" />






