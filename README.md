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
<p>

<br />
Add Two Virtual Machines to the Resource Group
<br />
<p>
First VM: Windows 10

- In the Azure portal, select "Virtual Machines" and create.
  
- For the Resource Group pick the one we previously made.
  
- Choose "Windows 10" from the available virtual machine templates.
  
- Configure VM settings such as name, size, and authentication method.
  
- Assign the VM to the newly created resource group(Make sure they are in the same Region, mine is West 2).
  
- Make sure you select a size with 2 or more vcpus.
  
- Keep track of your username and password.
  
-  Review configurations for the basics page, you can leave the rest of the pages as is and click "Create and review" to deploy the Windows 10 VM.

-  After verification click "Create" 
<p>
  
<img width="1474" alt="Screenshot 2024-10-31 at 3 41 16 PM" src="https://github.com/user-attachments/assets/45912a61-4436-4442-8f0a-25fd2de11b2d">
<img width="862" alt="Screenshot 2024-10-31 at 3 53 19 PM" src="https://github.com/user-attachments/assets/0f2a05eb-7ae8-4c73-a40c-86ccf8229568">

</p>

<br />
 
<p>
Second VM: Linux Ubuntu VM
  
- In the Azure portal, select "Virtual Machines" and create.

- For the Resource Group pick the one we previously made.

- Choose "Ubuntu Server 22.04" from the available virtual machine templates.
  
- Assign the VM to the newly created resource group(Make sure they are in the same Region, mine is West 2).
  
- Make sure you select a size with 2 or more vcpus.
  
- Keep track of your username and password.
  
- Before creating this VM, go to the network tab and make sure both of your VMs are in the same Virtual Network.
  
-  Review configurations for the basics page, and click "Create and review" to deploy the Linux Ubuntu VM.
  
-  After verification click "Create" 
  
  <img width="1239" alt="Screenshot 2024-10-31 at 5 09 35 PM" src="https://github.com/user-attachments/assets/4ed3b477-7e6b-4701-83ce-122ccda3c2dc">
  
  <img width="1262" alt="Screenshot 2024-10-31 at 5 17 06 PM" src="https://github.com/user-attachments/assets/253beae5-4709-4a9c-8ec3-4c7da376478e">
  
<img width="1259" alt="Screenshot 2024-10-31 at 5 21 59 PM" src="https://github.com/user-attachments/assets/1bed67cd-f741-4bae-be32-86a5427f3051">

Connect to Your Virtual Machine:

- Retrieve the Public IP Address: Once your VM is created, locate and note the public IP address assigned to it in the Azure Portal.

- Use Remote Desktop: Open the Remote Desktop Connection application on your local machine. (Downloand Microsoft remote desktop on mac from app store)

- Establish the Connection: Click the + icon add PC and enter the VM's public IP address in the Remote Desktop app.

- Enter password: Enter your previously made username and password.

  
<img width="1226" alt="Screenshot 2024-11-01 at 2 34 40 PM" src="https://github.com/user-attachments/assets/353f7a57-b334-4663-8c2b-681d3fcbd2fb">

<img width="473" alt="Screenshot 2024-11-01 at 2 32 51 PM" src="https://github.com/user-attachments/assets/354ff187-3ca9-41da-9257-7613304f22b0">

Observe ICMP Traffic

- Both virtual machines (VMs) have been successfully installed, and the Windows VM is connected via Microsoft Remote Desktop Protocol (RDP).
  
- Next, we will install Wireshark on our Windows VM. Wireshark is a free and open-source packet analyzer used for network troubleshooting, analysis, software and communications protocol development, and education.

- Open Microsoft Edge and paste the following URL into the address bar: https://www.wireshark.org.

- Click download and download the Windows x64 installer
  
<img width="1800" alt="Screenshot 2024-11-01 at 2 57 37 PM" src="https://github.com/user-attachments/assets/e6078756-ed87-4b0b-b78d-d24bf9e4850c">

<img width="757" alt="Screenshot 2024-11-01 at 3 04 50 PM" src="https://github.com/user-attachments/assets/eaf8bcde-73fb-4010-bc03-9114e9eba1e1">



</p>
<p>

</p>
<br />

<p>

</p>
<p>

</p>
<br />
