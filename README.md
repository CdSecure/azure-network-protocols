<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
Creating a Resource Group in Microsoft Azure

- Navigate to the Azure portal.
- Select "Resource groups" from the menu.
- Click on "Add" to create a new resource group.
- Enter a name and select a region for the resource group.
- Click "Review + create" and then "Create" to finalize.
<img width="1258" alt="Screenshot 2024-10-31 at 3 34 39 PM" src="https://github.com/user-attachments/assets/a670e8dd-9a46-4217-b10e-702658a1f54c">

<img width="1314" alt="Screenshot 2024-10-31 at 3 36 32 PM" src="https://github.com/user-attachments/assets/c1f60194-ba15-4164-8b9a-ca1d3b51c581">


<br />
Add Two Virtual Machines to the Resource Group

First VM: Windows 10
- In the Azure portal, select "Virtual Machines" and create.
- For the Resource Group pick the one we previously made. 
- Choose "Windows 10" from the available virtual machine templates.
- Configure VM settings such as name, size, and authentication method.
- Assign the VM to the newly created resource group.
- Review configurations and click "Create" to deploy the Windows 10 VM.
<img width="1474" alt="Screenshot 2024-10-31 at 3 41 16 PM" src="https://github.com/user-attachments/assets/45912a61-4436-4442-8f0a-25fd2de11b2d">
</p>

<br />

<p>

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
