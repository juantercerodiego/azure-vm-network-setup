<p align="center">
<img width="640" height="401" alt="Azure Virtual Network Diagram" src="https://github.com/user-attachments/assets/0b0e1076-eee6-4d86-a165-a2bc75365c89" />
</p>

<h1>Azure Virtual Machines & Network Infrastructure Setup</h1>

**Quick Note:** This project builds the foundational network structure for my cloud environment. Once this network is deployed, I use it to configure Active Directory, run automated user-onboarding scripts, and test client log-ins. You can view that next phase here: [https://github.com/juantercerodiego/server-setup-to-employee-login](https://github.com/juantercerodiego/server-setup-to-employee-login) <br />

### Project Overview
Think of this project as building a secure, private neighborhood in the cloud. Before a company can set up computers for its employees, it needs a safe, isolated space for those computers to live and talk to each other. 

In this project, I logged into Microsoft Azure (a cloud computing platform) and built that entire environment from scratch. I created a secure digital boundary, deployed a main corporate computer (the Server), set up a standard employee computer (the Client), and made sure their connection was locked down and permanent so they never lose touch.

<h2>Environments and Technologies Used</h2>

- **Microsoft Azure** (The cloud platform where the computers live)
- **Remote Desktop Connection** (The app used to log into and see these cloud computers)
- **Virtual Networks & Subnets** (The digital "wires" and boundaries connecting the machines)
- **Network Security Groups** (The digital security guards that block unwanted traffic)

<h2>Operating Systems Used </h2>

- **Windows Server 2025** (The main "brain" computer for the company)
- **Windows 11 Pro** (The standard computer an everyday employee would use)

<br />

---

<h2>How I Built It (Step-by-Step)</h2>

<h2>Step 1: Creating the Resource Group and Virtual Network (VNet)</h2>

**Before you buy furniture, you need a house with a front door. In the cloud, that house is your Virtual Network (VNet), and the plot of land it sits on is your Resource Group.**

<p align="center">
<img width="771" height="550" alt="Creating VNet in Azure Portal" src="https://github.com/user-attachments/assets/455fc62f-89a3-4e7b-bf6f-981af40c8ee3" />
</p>

1. Logged into my Microsoft Azure account portal.
2. Searched for **Virtual Networks** and clicked **Create**.
3. Created a new folder called a Resource Group (named **`Lab-RG`**) to keep all my project files organized in one neat pile.
4. Named my network **`Lab-VNet`**, chose a location server close to me for fast speeds, and left the standard network settings as they were. Clicked **Review + Create**.

#### ⭐ **Verification: Confirming the Network is Created** ⭐
<p align="center">
<img width="733" height="391" alt="VNet Deployment Confirmation" src="https://github.com/user-attachments/assets/54995b23-c44e-43e5-a3ea-a2acdd49bf18" />
</p>

<br />

---

<h2>Step 2: Deploying the Windows Server VM</h2>

**Next, I built the main power computer—the Server. This machine will eventually run the entire company network and hold all employee accounts.**

<p align="center">
<img width="647" height="600" alt="Configuring Server VM" src="https://github.com/user-attachments/assets/7ec5bfe5-6318-411d-9a55-f5dcd252b7b0" />
</p>

1. Searched for **Virtual Machines** (cloud computers) in Azure and clicked **Create**.
2. Picked my **`Lab-RG`** folder to make sure the computer was placed in the right spot.
3. Named the computer **`Server-VM`** and chose **Windows Server 2025** as the operating system.
4. Created a secure admin username and password so I could log in safely later.
5. Went to the **Networking** tab to make sure this computer was plugged into the **`Lab-VNet`** I built in Step 1. Left the rest on default and clicked Create.

#### ⭐ **Verification: Confirming the Server is Running** ⭐
<p align="center">
<img width="771" height="517" alt="Server VM Running State" src="https://github.com/user-attachments/assets/f75b7ec2-5a6a-43f8-95ba-0023cf9fbc10" />
</p>

<br />

---

<h2>Step 3: Deploying the Windows 11 Pro Client VM</h2>

**With the server built, I needed a standard workstation computer to represent a regular employee sitting at their office desk.**

<p align="center">
<img width="767" height="600" alt="Configuring Client VM" src="https://github.com/user-attachments/assets/d696f209-1816-4a9c-8301-114cff6b9164" />
</p>

1. Followed the exact same steps to create a second Virtual Machine.
2. Named this workstation **`Client-VM`** and chose **Windows 11 Pro** as the operating system.
3. Under the **Networking** tab, I made absolutely sure it was hooked up to the exact same **`Lab-VNet`** as the server. *(This is crucial: if they aren't on the same network, they are in different worlds and can't talk to each other!)*
4. Clicked Create and waited for the computer to finish booting up in the cloud.

#### ⭐ **Verification: Confirming the Employee Workstation is Running** ⭐
<p align="center">
<img width="876" height="352" alt="Client VM Running State" src="https://github.com/user-attachments/assets/f7c86be6-e883-4575-bb7e-59ae6c703751" />
</p>

<br />

---

<h2>Step 4: Setting a Static Private IP for the Server</h2>

**In a real business, the server's digital address (IP address) cannot change. If it changes dynamically, the employee computers will get confused, lose the connection, and won't be able to log in. I had to lock the server's address permanently in place.**

<p align="center">
<img width="592" height="600" alt="Modifying IP Configuration to Static" src="https://github.com/user-attachments/assets/52be9c82-44c3-451c-8e5d-071451abf5c7" />
</p>

1. In the Azure Portal, went to the main page for the **`Server-VM`**.
2. Clicked on **Networking** on the left menu, then clicked on the server's primary network card link.
3. Opened **IP configurations** and clicked on the settings line.
4. Changed the setting from **Dynamic** (which means the address changes randomly) to **Static** (which means permanent).
5. Saved the changes. Now the server will keep the exact same digital address forever, ensuring the client computer always knows exactly where to find it.

#### ⭐ **Verification: Confirming the Address is Locked In** ⭐
<p align="center">
<img width="447" height="284" alt="Static IP Assignment Complete" src="https://github.com/user-attachments/assets/6293c4d8-3e4c-4472-b30e-f36ff0aa433b" />
</p>
