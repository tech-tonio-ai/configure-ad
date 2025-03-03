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
<img src="https://i.imgur.com/pU5A58S.png" alt="create virtual network"/>
</p>


## Create the Domain Controller VM (Windows Server 2022)
- **VM Name:** `DC-1`
- **Username:** `labuser`
- **Password:** `Cyberlab123!`
- After VM is created, set the Domain Controller’s NIC Private IP address to be **static**.
- Log into the VM and **disable the Windows Firewall** (for testing connectivity).

---

# Setup Client-1 in Azure

## Create the Client VM (Windows 10)
- **VM Name:** `Client-1`
- **Username:** `labuser`
- **Password:** `Cyberlab123!`
- Attach it to the **same region and Virtual Network** as `DC-1`.
- After VM is created, set `Client-1`’s **DNS settings** to `DC-1`’s **Private IP address**.
- From the Azure Portal, **restart** `Client-1`.

## Verify Connectivity
1. **Login** to `Client-1`.
2. Attempt to **ping** `DC-1`’s private IP address.
3. Ensure the **ping succeeded**.
4. From `Client-1`, open **PowerShell** and run:
   ```powershell
   ipconfig /all
   ```
5. The output for the **DNS settings** should show `DC-1`’s private IP Address.

