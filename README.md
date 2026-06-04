
<p align="center">
<img width="640" height="401" alt="1_YNS5204KzMZTNiO2AhG0NQ" src="https://github.com/user-attachments/assets/0b0e1076-eee6-4d86-a165-a2bc75365c89" />


</p>

<h1>Azure Virtual Machines & Network Infrastructure Setup</h1>

This project is the foundation for all my cloud lab experiments. Before managing users or inspecting traffic, I needed to build the digital workspace. I deployed two virtual machines in Microsoft Azure, configured a custom Virtual Network (VNet), and adjusted internal IP addresses so the machines could talk to each other securely.<br />




<h2>Environments and Technologies Used</h2>

- **Microsoft Azure** (Cloud Platform)
- **Remote Desktop** (RDP)
- **Virtual Networks (VNets) & Subnets**
- **Network Security Groups** (NSGs)

<h2>Operating Systems Used </h2>

- **Windows Server 2022** (Soon To Be Domain Controller)
- **Windows 11** (Soon To Be Employee Workstation)

<h2>What You Need Before Starting (Prerequisites)</h2>

- **An Azure Account:** You need an active subscription to build the virtual machines.
- **Remote Desktop Connection (RDP):** Built into Windows or can be downloaded on a Mac to connect to the VMs. 

<h2>How I Built It (Step-by-Step)</h2>
<h2>Step 1: Creating the Resource Group and Virtual Network (VNet)</h2>

<p>
<img width="771" height="650" alt="Screenshot 2026-06-03 111700" src="https://github.com/user-attachments/assets/4c7ca829-d5d2-4cbb-8e38-bb2727aacf86" />




</p>
<p>
  
**Before managing any users, I needed to turn my basic Windows Server into a master Domain Controller.**
  
**1:** Logged into the Azure Portal.
  
**2:** Searched for Virtual Networks and clicked Create.

**3:** Created a new Resource Group (like Lab-RG) to keep all my project files in one neat pile.

**4:** Named the VNet (like Lab-VNet), chose a region close to me, and left the default IP address space settings. Hit Review + Create.

</p>
<br />
<h2>Step 2: Deploying the Windows Server VM </h2>
<p>
<img width="783" height="500" alt="Screenshot 2026-05-13 115239" src="https://github.com/user-attachments/assets/269985ec-2a11-4ad2-a58f-f8af5521ac7c" />

</p>
<p>
  
**Next, I built the main server machine that will eventually run the whole company network.**
  
**1:** Searched for Virtual Machines in Azure and clicked Create -> Azure Virtual Machine.
  
**2:** Selected my Lab-RG resource group, named the machine (like Server-VM), and chose Windows Server 2025 as the image.

**3:** Set up my administrator username and password (wrote these down so I didn't get locked out!).

**4:** Under the Networking tab, made sure it was hooked up to the Lab-VNet I built in Step 1. Left the other defaults and hit Create.


</p>
<br />
<h2>Step 3: Deploying the Windows 10 Client VM</h2>
<p>
<img width="808" height="548" alt="Screenshot 2026-05-13 120309" src="https://github.com/user-attachments/assets/5f565de1-eace-4bd0-bdf0-4ee7670fff02" />



</p>
<p>
  
**With the server built, I needed a standard workstation computer to represent an everyday employee.**
  
**1:** Followed the exact same steps to create a second Virtual Machine.
  
**2:** Named this one Client-VM and chose Windows 10 Pro as the operating system image.

**3:** Under the Networking tab, I made absolutely sure it was assigned to the exact same Lab-VNet as the server. (If they aren't on the same network, they can't talk!).

**4:** Hit Create and waited for the deployment to finish.
</p>
<br />
<h2>Step 4: Setting a Static Private IP for the Server</h2>
<p>
<img width="623" height="570" alt="Screenshot 2026-05-13 123209" src="https://github.com/user-attachments/assets/f2ffb586-702b-463e-9161-3ca84411c913" />



</p>
<p>
  
**In a real business, the server's address cannot change, or the employee computers will get confused and lose connection. I had to lock the server's IP address in place.**
  
**1:** In the Azure Portal, went to my Server-VM page.
  
**2:** Clicked on Networking on the left menu, then clicked on the server's Network Interface (NIC).

**3:** Went to IP configurations, clicked on the primary configuration, and changed the assignment from Dynamic (changing) to Static (permanent).

**4:** Saved the changes. Now the server will keep the exact same private IP address forever.


</p>
<br />




