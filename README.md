<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


# Setup Domain Controller in Azure

## Create a Resource Group
<p align="center">
<img src="https://i.imgur.com/5vpfAZN.png" alt="setup resource group"/>
</p>


## Create a Virtual Network and Subnet
<p align="center">
  <img src="https://i.imgur.com/5HyCRQ5.png" alt="Image 1" width="45%"/>
  <img src="https://i.imgur.com/UhpWcQr.png" alt="Image 2" width="45%"/>
</p>


## Create the Domain Controller VM (Windows Server 2022)
- **VM Name:** `DC-1`
- **Username:** `labuser`
- **Password:** `Cyberlab123!`
<p align="center">
  <img src="https://i.imgur.com/717dY3o.png" width="30%" />
  <img src="https://i.imgur.com/49Tehdn.png" width="30%" />
  <img src="https://i.imgur.com/pqUTA4B.png" width="30%" />  
</p>

- Log into the VM dc-1 and **disable the Windows Firewall** (for testing connectivity).

---

# Setup Client-1 in Azure

## Create the Client VM (Windows 10)
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

## Verify Connectivity
1. **Login** to `Client-1`.
2. Attempt to **ping** `DC-1`’s private IP address.
3. Ensure the **ping succeeded**.
4. From `Client-1`, open **CMD** and run:
   ```cmd
   ipconfig /all
   ```
5. The output for the **DNS settings** should show `DC-1`’s private IP Address.
<p align="center">
  <img src="https://i.imgur.com/UkdxC5J.png" alt="Image 1" width="45%"/>
  <img src="https://i.imgur.com/Q5VQTdn.png" alt="Image 2" width="45%"/>
</p>
