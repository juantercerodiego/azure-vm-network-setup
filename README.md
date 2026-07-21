<p align="center">
<img width="640" height="401" alt="Azure Virtual Network Diagram" src="https://github.com/user-attachments/assets/0b0e1076-eee6-4d86-a165-a2bc75365c89" />
</p>

<h1>Azure Virtual Machines & Network Infrastructure Setup</h1>

**Quick Note:** This project builds the foundational network structure for my cloud environment. Once this network is deployed, I use it to configure Active Directory, run automated user-onboarding scripts, and test client log-ins. You can view that next phase here: [https://github.com/juantercerodiego/server-setup-to-employee-login](https://github.com/juantercerodiego/server-setup-to-employee-login) <br />

### What This Project Does
Think of this project as building a secure, private neighborhood in the cloud. Before a company can set up computers for its employees, it needs a safe, isolated space for those computers to live and talk to each other. 

In this project, I logged into Microsoft Azure and built that entire environment from scratch. I created a secure network space, built a main corporate computer (**`Server-VM`**), built a standard employee workstation (**`Client-VM`**), and locked the server's network address in place so the machines never lose connection with each other.

<h2>Environments and Technologies Used</h2>

- **Microsoft Azure** (The cloud platform where the computers are hosted)
- **Virtual Networks (VNets) & Subnets** (The digital wires and boundaries connecting the machines)
- **Network Security Groups (NSGs)** (The digital security guards that block unwanted traffic)

<h2>Languages Used</h2>

- **N/A** (GUI-based Cloud Infrastructure Deployment)

<h2>Operating Systems Used </h2>

- **Windows Server 2025** (The main "brain" computer for the company)
- **Windows 11 Pro** (The standard computer an everyday employee would use at their desk)

<h2>What You Need Before Starting (Prerequisites)</h2>

- **An Azure Account:** You need an active subscription to build the virtual machines.

<br />

---

<h2>Phase 0: Activating Your Azure Subscription</h2>

Before you can build anything in Azure, you have to activate a subscription. This tells Azure how to handle your account access and lab resources. If you don't have one set up yet, here is exactly how I configured mine:

1. Logged into the **Azure Portal**.
2. Searched for **Subscriptions** in the top search bar and clicked **Add**.
3. On the **Basics** tab, gave the subscription a descriptive name (like `Lab-Subscription`).
4. Selected my billing account, billing profile, and invoice section from the dropdowns. 
5. Under the **Plan** options, chose **Microsoft Azure Plan for DevTest** (since this is an isolated training and testing environment) and kept the default advanced settings.

#### **Configuration Screenshot:**
<p align="center">
<img width="953" height="631" alt="1" src="https://github.com/user-attachments/assets/799d6d99-da98-483a-9176-37a566e17105" />

</p>

6. Added **Tags** (Name/Value pairs) to keep track of resource costs, then clicked **Review + Create**.

#### **Validation Passed Screenshot:**
<p align="center">
<img width="977" height="872" alt="2" src="https://github.com/user-attachments/assets/80e03a51-1941-42b2-bab9-41c46a418aed" />

</p>

7. Once the portal verified the settings and gave a **Validation Passed** message, clicked **Create**. 

#### ⭐ **Verification of Successful Subscription Activation** ⭐
<p align="center">
<img width="747" height="491" alt="3" src="https://github.com/user-attachments/assets/9dbeda94-c368-4cd3-a613-9682b1560c13" />

</p>

*Note: Once it finishes deploying, you will see a "Successfully created the subscription" notification at the top right. Click **Go to subscription** to view it. If it doesn't show up in your main list right away, make sure your portal view filter isn't hiding it!*

<br />

---

<h2>How I Built It (Step-by-Step Infrastructure Setup)</h2>

<h2>Step 1: Creating the Resource Group and Virtual Network (VNet)</h2>

Before buying furniture (the virtual machines), you need a house and a front door. In Azure, that house is your Virtual Network (VNet), and the plot of land it sits on is your Resource Group.

1. Logged into the Azure Portal.
2. Searched for **Virtual Networks** and clicked **Create**.
3. Created a new Resource Group folder named **`Lab-RG`** to keep all my project files organized in one neat pile.
4. Named the VNet **`Lab-VNet`**, chose a region close to me for fast speeds, left the default IP address settings as they were, and hit **Review + Create**.

#### **Configuration Screenshot:**
<p align="center">
<img width="771" height="550" alt="Creating VNet in Azure Portal" src="https://github.com/user-attachments/assets/455fc62f-89a3-4e7b-bf6f-981af40c8ee3" />
</p>

#### ⭐ **Verification of Successful Network Deployment** ⭐
<p align="center">
<img width="733" height="391" alt="VNet Deployment Confirmation" src="https://github.com/user-attachments/assets/54995b23-c44e-43e5-a3ea-a2acdd49bf18" />
</p>

<br />

---

<h2>Step 2: Deploying the Windows Server VM </h2>

Next, I built the main server machine (**`Server-VM`**) that will eventually run the whole company network.

1. Searched for **Virtual Machines** in Azure and clicked **Create** -> **Azure Virtual Machine**.
2. Selected my **`Lab-RG`** resource group folder so the computer went to the right spot.
3. Named the machine **`Server-VM`** and selected **Windows Server 2025** as the operating system image.
4. Set up my administrator username and password (and safely wrote them down so I wouldn't get locked out!).
5. Under the **Networking** tab, made sure it was hooked up directly to the **`Lab-VNet`** I built in Step 1. Left the other defaults and hit **Create**.

#### **Configuration Screenshot:**
<p align="center">
<img width="647" height="600" alt="Configuring Server VM" src="https://github.com/user-attachments/assets/7ec5bfe5-6318-411d-9a55-f5dcd252b7b0" />
</p>

#### ⭐ **Verification of Successful Server Deployment** ⭐
<p align="center">
<img width="771" height="517" alt="Server VM Running State" src="https://github.com/user-attachments/assets/f75b7ec2-5a6a-43f8-95ba-0023cf9fbc10" />
</p>

<br />

---

<h2>Step 3: Deploying the Windows 11 Pro Client VM</h2>

With the server built, I needed a standard workstation computer (**`Client-VM`**) to represent an everyday employee sitting at their office desk.

1. Followed the exact same steps to create a second Virtual Machine.
2. Named this workstation **`Client-VM`** and selected **Windows 11 Pro** as the operating system image.
3. Under the **Networking** tab, I made absolutely sure it was assigned to the exact same **`Lab-VNet`** as the server. *(If they aren't on the same network, they are in completely different worlds and can't communicate!)*.
4. Hit **Create** and waited for the computer to finish setup.

#### **Configuration Screenshot:**
<p align="center">
<img width="767" height="600" alt="Configuring Client VM" src="https://github.com/user-attachments/assets/d696f209-1816-4a9c-8301-114cff6b9164" />
</p>

#### ⭐ **Verification of Successful Client Deployment** ⭐
<p align="center">
<img width="876" height="352" alt="Client VM Running State" src="https://github.com/user-attachments/assets/f7c86be6-e883-4575-bb7e-59ae6c703751" />
</p>

<br />

---

<h2>Step 4: Setting a Static Private IP for the Server</h2>

In a real business, the server's address cannot change, or the employee computers will get confused and lose connection. I had to lock the **`Server-VM`** IP address permanently in place.

1. In the Azure Portal, navigated to the **`Server-VM`** overview page.
2. Clicked on **Networking** on the left menu, then clicked on the server's primary network card link (**Network Interface**).
3. Went to **IP configurations** and clicked on the settings line.
4. Changed the assignment setting from **Dynamic** (which changes randomly) to **Static** (which is permanent).
5. Saved the changes. Now the server will keep the exact same private network address permanently, making sure the client computer always knows where to find it.

#### **Configuration Screenshot:**
<p align="center">
<img width="592" height="600" alt="Modifying IP Configuration to Static" src="https://github.com/user-attachments/assets/52be9c82-44c3-451c-8e5d-071451abf5c7" />
</p>

#### ⭐ **Verification of Successful Static IP Assignment** ⭐
<p align="center">
<img width="447" height="284" alt="Static IP Assignment Complete" src="https://github.com/user-attachments/assets/6293c4d8-3e4c-4472-b30e-f36ff0aa433b" />
</p>
