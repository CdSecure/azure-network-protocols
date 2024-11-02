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

Installing Wireshark

- Both virtual machines (VMs) have been successfully installed, and the Windows VM is connected via Microsoft Remote Desktop Protocol (RDP).

- Next, we will install Wireshark on the Windows VM. Wireshark is a free and open-source packet analyzer used for network troubleshooting, analysis, software and communications protocol development, and education.

- Open Microsoft Edge and enter the following URL into the address bar: https://www.wireshark.org.

- Click on "Download" and select the Windows x64 installer to begin the download.

- After the download is complete, run the installer and click "Next" through all the prompts until the installation is finished.

- Wireshark is now fully installed.
  
<img width="1800" alt="Screenshot 2024-11-01 at 2 57 37 PM" src="https://github.com/user-attachments/assets/e6078756-ed87-4b0b-b78d-d24bf9e4850c">

<img width="757" alt="Screenshot 2024-11-01 at 3 04 50 PM" src="https://github.com/user-attachments/assets/eaf8bcde-73fb-4010-bc03-9114e9eba1e1">

Observing ICMP Traffic

- With Wireshark open, select "Ethernet" and then click the shark fin icon at the top right to start capturing.

- Once the capture begins, you will see various types of network traffic representing the background activity within the Windows VM.

- To focus on ICMP traffic only, type "ICMP" into the top search bar and press Enter.

<img width="1124" alt="Screenshot 2024-11-02 at 5 04 26 PM" src="https://github.com/user-attachments/assets/6d0b1843-e4b4-47eb-a87c-7904b764e110">

<img width="1144" alt="Screenshot 2024-11-02 at 5 24 46 PM" src="https://github.com/user-attachments/assets/a810d201-894d-4af2-ba7e-1acd0103b3c2">

Establishing Network Traffic

- Currently, there is no network traffic being captured. To generate traffic, we will ping our Linux virtual machine (VM).

- Navigate back to Microsoft Azure, select the previously created Linux VM, and scroll down to locate its private IP address

<img width="941" alt="Screenshot 2024-11-02 at 5 42 28 PM" src="https://github.com/user-attachments/assets/f4740242-44a2-4916-9fd8-9ec4619fdb59">

- Next, we will ping our Linux virtual machine (VM).

- Click on the Start menu at the bottom left and open PowerShell.

- In PowerShell, type ping followed by the Linux VM's private IP address.

- In Wireshark, you should see the ICMP traffic between the Windows VM and the Linux VM, displaying four requests and four replies.
  
<img width="1800" alt="Screenshot 2024-11-02 at 5 45 50 PM" src="https://github.com/user-attachments/assets/76c71ad6-f7c4-4c23-8692-562ebf19cdfe">

Configuring a Firewall

- We will now configure a firewall to prevent the Windows VM from pinging the Linux VM.

- First, we will initiate a continuous ping from the Windows VM to the Linux VM.

- To start a continuous ping, open PowerShell and type ping "IP-address" -t, replacing "IP-address" with the Linux VM's private IP address. You should see continuous ping traffic occurring in the background.

<img width="859" alt="Screenshot 2024-11-02 at 6 23 21 PM" src="https://github.com/user-attachments/assets/657d50e7-0144-48f8-a9fc-02ad35683a1a">

Blocking Incoming Ping Traffic

- We will now block all incoming ping (ICMP) traffic from the Windows VM.

- Navigate back to the Azure portal and select your Linux virtual machine (VM).

- In the left-hand column, go to Networking under Network Settings. Within this section, locate and click on the Network Security Group, which serves as the firewall for your VM.


<img width="816" alt="Screenshot 2024-11-02 at 6 29 19 PM" src="https://github.com/user-attachments/assets/92e3f8e2-01c5-4237-a22c-6d304e70b33d">

<img width="866" alt="Screenshot 2024-11-02 at 6 31 18 PM" src="https://github.com/user-attachments/assets/a2f1557b-394f-4146-841f-34e9a800bf80">

- In the left column, select Inbound security rules; we will create a new rule for inbound traffic. Click on the Add button at the top of the page.

<img width="1008" alt="Screenshot 2024-11-02 at 6 32 59 PM" src="https://github.com/user-attachments/assets/bae5710d-152d-4f22-bf26-21ad5f819e5d">

<img width="841" alt="Screenshot 2024-11-02 at 6 37 22 PM" src="https://github.com/user-attachments/assets/bb0805d7-e28d-4fda-a698-c3cb54d681fa">
Configuring the Inbound Security Rule

- Set up the inbound security rule with the following configurations, column by column:

- Source: Select Any, since we want to block ICMP traffic from any source.

- Source Port Ranges: Enter an asterisk (*), which represents any port.

- Destination and Service: Leave these settings at their default values.

- Protocol: Choose Icmp4 to block ICMP traffic.

- Action: Select Deny to prevent the specified traffic.

- Priority: Set the priority to 290 so that this rule overrides previous rules.

- After completing all configurations, click Add to create the rule.
<img width="578" alt="Screenshot 2024-11-02 at 6 38 09 PM" src="https://github.com/user-attachments/assets/cbd51e5e-ee72-4357-a9df-77e61879c9b3">

- It may take some time for the firewall rule to propagate, but you will notice that the pings cease, and you begin receiving "Request timed out" messages. This indicates that the Linux VM is no longer accepting ICMP traffic from any source.

- In Wireshark, you will observe that the Windows VM continues to send ICMP requests but does not receive any replies.

<img width="1800" alt="Screenshot 2024-11-02 at 6 46 49 PM" src="https://github.com/user-attachments/assets/5adc9c35-5edb-417f-8b38-26bd8a3553a4">

- We have just observed how ICMP traffic goes through Windows VM and Linux VM, We have blocked that traffic as well.

- We will now re-enable that traffic by removing the rule we made.

- We can just click delete 

- Once deleted you can head back to the Windows VM and see the traffic begin to flow again.

- To completely stop the ping press control C

<img width="927" alt="Screenshot 2024-11-02 at 6 56 11 PM" src="https://github.com/user-attachments/assets/483a329b-f01d-4269-b5cc-e04983c8a6a0">

<img width="1800" alt="Screenshot 2024-11-02 at 6 58 05 PM" src="https://github.com/user-attachments/assets/74841868-ad81-413d-9ba4-6c41a4db5db2">

</p>
<br />

<p>

</p>
<p>

</p>
<br />
