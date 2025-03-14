[<-- PREVIOUS: AZURE SETUP](https://github.com/tech-tonio-ai/azure-seup)
--
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Deploying Active Directory in Azure: A Cloud-Based Implementation</h1>
This guide covers the deployment of an on-premises-style Active Directory environment using Azure Virtual Machines, enabling centralized identity and access management in the cloud.<br />
<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- CMD/PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

Step 1 : Setup Domain Controller in Azure
    - Create a Resource Group
    
Step 2 : Create a Virtual Network and Subnet

Step 3 : Create the Domain Controller VM (Windows Server 2022)

Step 4 : Setup Client-1 in Azure

Step 5 : Verify Connectivity

Step 6 : Install Active Directory 


<h2>Deployment and Configuration Steps</h2>


### 1.Setup Domain Controller in Azure

#### Create a Resource Group
<p align="center">
<img src="https://i.imgur.com/5vpfAZN.png" alt="setup resource group"/>
</p>


### 2.Create a Virtual Network and Subnet
<p align="center">
  <img src="https://i.imgur.com/5HyCRQ5.png" alt="Image 1" width="45%"/>
  <img src="https://i.imgur.com/UhpWcQr.png" alt="Image 2" width="45%"/>
</p>


### 3.Create the Domain Controller VM (Windows Server 2022)
- **VM Name:** `DC-1`
- **Username:** `labuser`
- **Password:** `Cyberlab123!`
<p align="center">
  <img src="https://i.imgur.com/717dY3o.png" width="30%" />
  <img src="https://i.imgur.com/49Tehdn.png" width="30%" />
  <img src="https://i.imgur.com/pqUTA4B.png" width="30%" />  
</p>

- Log into the VM dc-1 
<p align="center">
<img src="https://i.imgur.com/8P3vyaB.png" alt="dc-1"/>
</p>
 <h3>Disable the Windows Firewall(for testing connectivity).</h3>
<p align="center">
  <img src="https://i.imgur.com/qOJQxva.png" width="45%" />
  <img src="https://i.imgur.com/kBvK0VP.png" width="33%" />
</p>


### 4.Setup Client-1 in Azure

#### Create the Client VM (Windows 10)
- **VM Name:** `Client-1`
- **Username:** `labuser`
- **Password:** `Cyberlab123!`
- Attach it to the **same region and Virtual Network** as `DC-1`.
<p align="center">
<img src="https://i.imgur.com/cBQdeE3.png" alt="client-1"/>
</p>
- After VM is created, set `Client-1`’s **DNS settings** to `DC-1`’s **Private IP address**.
<p align="center">
  <img src="https://i.imgur.com/AkByKnY.png" alt="Image 1" width="45%"/>
  <img src="https://i.imgur.com/EdqWFQs.png" alt="Image 2" width="45%"/>
</p>
- From the Azure Portal, **restart** `Client-1`.

### 5.Verify Connectivity
- **Login** to `Client-1`.
- Attempt to **ping** `DC-1`’s private IP address.
- Ensure the **ping succeeded**.
- From `Client-1`, open **CMD** and run:
   ```cmd
   ipconfig /all
   ```
- The output for the **DNS settings** should show `DC-1`’s private IP Address.
<p align="center">
  <img src="https://i.imgur.com/UkdxC5J.png" alt="Image 1" width="45%"/>
  <img src="https://i.imgur.com/Q5VQTdn.png" alt="Image 2" width="45%"/>
</p>

### 6. InstallActive Directory Admin and User Management 
   
- Login to DC-1 and install Active Directory Domain Services
<p align="center">
  <img src="https://i.imgur.com/SWXkR0v.png" alt="Image 1" width="45%"/>  
</p>
- Promote as a DC
<p align="center">
  <img src="https://i.imgur.com/FUkZou6.png" alt="Image 1" width="45%"/>  
</p>

- Setup a new forest as `mydomain.com` and set a password:
<p align="center">
  <img src="https://i.imgur.com/hO5L8NY.png" width="30%" />
  <img src="https://i.imgur.com/bdfLJJh.png" width="30%" />
  <img src="https://i.imgur.com/vyu3m4F.png" width="30%" />  
</p>

- Restart and then log back into DC-1 as user: `mydomain.com\labuser`.
<p align="center">
  <img src="https://i.imgur.com/d98Ffyn.png" alt="Image 1" width="45%"/>  
</p>

[NEXT: AZURE ADMIN and USER MANAGEMENT -->](https://github.com/tech-tonio-ai/active-directory-admin-and-user-mngmnt)
