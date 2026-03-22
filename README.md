# Azure Sentinel (SIEM) Honeypot Home Lab

<img width="358" height="198" alt="image" src="https://github.com/user-attachments/assets/1b3be7ab-5057-491b-a6ca-2d4f819138a7" />

# Project Summary 

Deployed an Azure-based honeypot integrated with Microsoft Sentinel to capture and analyze real-world attack traffic. Developed KQL-based detections for brute-force activity, authentication anomalies, and geolocation-based attack patterns. Built a SOC-style dashboard to visualize attacker behavior and global threat distribution.

# Description

Deployed an Azure-based honeypot integrated with Microsoft Sentinel to capture and analyze real-world attack traffic. Developed KQL-based detections for brute-force activity, authentication anomalies, and geolocation-based attack patterns. Built a SOC-style dashboard to visualize attacker behavior and global threat distribution.

 
# Learning Objectives 

Azure Honeypot with Microsoft Sentinel – Attack Detection &amp; Visualization Dashboard

- Deploy a cloud-based honeypot using Azure Virtual Machines

- Configure log ingestion into Log Analytics Workspace

- Develop KQL queries to detect authentication events (Event IDs 4624, 4625)

- Identify brute-force and credential spraying patterns

- Enrich logs with geolocation data for threat analysis

- Build SOC-style dashboards using Microsoft Sentinel Workbooks



# Step 1: Create a Microsoft Azure Account

- Microsoft offers $200 in Azure credit for 30 days when you first initally sign up (You will need to attach a credit card in order to sign up for the free trial but you can cancel it before your trial ends)

# Step 2: Create a Resource Group

- Name your resource group, click review + create 

 <img width="1076" height="1754" alt="Creating-Resource-Group" src="https://github.com/user-attachments/assets/100d1134-4cee-438d-8a8d-1d219c37f48e" />

 # Step 3: Create Virtual Network

<img width="1079" height="1753" alt="Creating-Virtual-Network" src="https://github.com/user-attachments/assets/fa0314be-d9b9-4d26-90b6-d34dd49b16cd" />
<img width="1078" height="1708" alt="Creating-Virtual-Network2" src="https://github.com/user-attachments/assets/bbc8cf41-6436-445e-9e4c-deddfd1a72f2" />
<img width="1075" height="1754" alt="Creating-Virtual-Network3" src="https://github.com/user-attachments/assets/55ce932b-e874-40ff-a4af-74d9414590ec" />
<img width="1078" height="1711" alt="Creating-Virtual-Network4" src="https://github.com/user-attachments/assets/577abb0d-42b1-42ec-bc52-b6fb223f491a" />

# Step 4: Create Vulnerable Virtual Machine

# Virtual Machine Details

- Give your Virtual Machine a name (CORP-LAPTOP-EAST09)
- Choose your region (US-EAST2)
- Availability Options: No Infrastructure Redundancy
- Security Type: Standard
- Image: Windows 10 Enterprise, version 22H2 - x64 Gen1 (free services eligible)
- Size: Default

# Administrator Account: 

- Set up a username and password for the virtual machine
- The account and password you set for this virtual machine is the same credentials you will use when we remote into the VM via RDP

<img width="1073" height="1712" alt="Creating-Virtual-Machine" src="https://github.com/user-attachments/assets/89d47863-4338-4d38-a1b9-8e0c7c5e5781" />
<img width="1076" height="1712" alt="Creating-Virtual-Machine2" src="https://github.com/user-attachments/assets/addde12b-a751-44b8-aaee-5560e0c1cc04" />
<img width="1077" height="1713" alt="Creating-Virtual-Machine3" src="https://github.com/user-attachments/assets/2482a053-28a6-4d87-b1c2-db9bbbd2b045" />
<img width="1077" height="1713" alt="Creating-Virtual-Machine4" src="https://github.com/user-attachments/assets/bb94cb76-4812-40fb-a9d5-97c9e07bbf2c" />

# Step 5: Check Resource Groups 

- Verify that the resources you had created within Azure are in the same region and resource group

<img width="1076" height="1749" alt="Verify-Resource-Creations" src="https://github.com/user-attachments/assets/6905a64d-4a67-4463-99cd-c1904b303ebc" />

# Step 6: Configure NSG (Network Security Group) 

- Select NSG in the resource group 
- Delete the current RDP inbound rule
- Create an Inbound Security Rule allowing any traffic to the VM:
- The rule should look like this when creating it:

<img width="1078" height="1863" alt="Configuring-NSG" src="https://github.com/user-attachments/assets/3dfcceef-f6b7-460b-8985-184d1f3bb137" />

# Step 7: Connect to the VM via RDP

- In the resource group, if you click on the VM on the right pane it will display the public IP assigned to that VM 

<img width="1078" height="1744" alt="VM-Public-IP" src="https://github.com/user-attachments/assets/42d0d35c-6100-4325-b330-5b30a5b00475" />

# Step 8: Turn off Windows Firewall on VM 

- Once you are remoted to the VM navigate to Windows Defense Firewall with Advanced Features and click on Windows Defender Firewall properties

<img width="1076" height="781" alt="Windows-Defender-Firewall-Proprerties" src="https://github.com/user-attachments/assets/2be1ce98-36a4-4a2c-97f6-c4d6c509724d" />

- The pane that pops up will display 4 tabs: Domain Profile, Private Profile, Public Profile and IPsec Settings. Disable Domain, Private and Public Profile

<img width="403" height="461" alt="Windows-Defender-Firewall-Proprerties2" src="https://github.com/user-attachments/assets/f3cfb579-c4bc-4ee7-86e5-6ddf8b35a94b" />

# Step 9: Ping VM 

- Once the firewall on the VM has been disabled, on your desktop attempt to ping the VM.
- Ping the IP that was assinged to your VM 

<img width="523" height="211" alt="Ping-VM" src="https://github.com/user-attachments/assets/6d60a5a8-3884-4470-ba50-b9b48c450f53" />

# Step 10: Create Log Analytics Workspace

- In Microsoft Azure go into the search bar and look up "Log Analytics Workspace"
- Create a new workspace

<img width="1076" height="1751" alt="Creating-LAW" src="https://github.com/user-attachments/assets/4b359f98-37c9-475c-81b1-42bdba112ca9" />

# Step 11: Add Log Analytics Workspace you created to Microsoft Sentinel

- Navigate to Microsoft Sentinel and add a workspace

<img width="1079" height="1752" alt="Adding-LAW-To-Sentinel" src="https://github.com/user-attachments/assets/c69a1b45-343a-4e99-bfcb-a45aaf3283d8" />

# Step 12: Install Windows Security Events from the content hub on Microsoft Sentinel

- Navigate to Microsoft Sentinel and navigate to the Content Hub
- The content hub has been transitioned to Microsoft XDR
- Once in the Content Hub search for Windows Security Events 

<img width="1076" height="1748" alt="Install-Windows-Security-Events-Contenthub" src="https://github.com/user-attachments/assets/542bf366-3af1-43d2-8f43-74bc40406fb6" />

# Step 13: Configure Windows Security Events via AMA

- After installing Windows Security Events via Content Hub click on Manage
- Select Windows Security Events via AMA and open connector page 

<img width="1917" height="912" alt="Windows-Security-Events-Connector-Page" src="https://github.com/user-attachments/assets/6f5b88db-14a4-410f-a1f3-f81ebd9a8803" />


# Step 14: Create Data Collection Rule

- Name the data colletion rule
- Select Subscription
- Select Resource Group
- Select types of events

<img width="1078" height="1747" alt="Data-Collection-Rule1" src="https://github.com/user-attachments/assets/23abae35-7022-4a04-b18a-2ccb7a3dadd0" />
<img width="1069" height="965" alt="Data-Collection-Rule2src="https://github.com/user-attachments/assets/e15352aa-aba4-4af2-a9cd-6a7dc0a68ebc" />
<img width="1079" height="956" alt="Data-Collection-Rule3" src="https://github.com/user-attachments/assets/eec9f5eb-9275-4100-aab6-cb19f2db8e6d" />
<img width="1078" height="974" alt="Data-Collection-Rule4" src="https://github.com/user-attachments/assets/f4cf6820-3cd7-42b7-8096-de9218280f9d" />

# Step 15: Verify Monitoring Azure Agent is installed on VM

- Navigate to your virtual machine, on the left pane click the settings drop down menu and click on "Extensions + Applications"
- In the Extensions + Applications page this should be displayed: 

<img width="1078" height="997" alt="Extensions + Applications" src="https://github.com/user-attachments/assets/874abd81-e3f6-4145-bcad-e33fd5f39ec2" />

# Setp 16: Verify the logs are being forwarded to the Log Analytics Workspace 

- Navigate to the Log Analytics Workspace and on the left click on logs

<img width="1916" height="908" alt="Verifying-Logs-Are-Being-Forwarded" src="https://github.com/user-attachments/assets/d778b478-7697-4890-b408-75f6e7bfbfe0" />

# Step 17: Create a workbook in Microsoft Sentinel

- Delete the default populated charts
- Save the workbook and give it a title
- Open the workbook in azure 

<img width="1914" height="907" alt="Create-Workbook-In-Sentinel1" src="https://github.com/user-attachments/assets/96cb80f1-d770-42d1-be95-28e87887749c" />
<img width="1912" height="452" alt="Create-Workbook-In-Sentinel2" src="https://github.com/user-attachments/assets/37abe7b1-9215-4cb3-bca4-e1751934d75e" />
<img width="1919" height="905" alt="Create-Workbook-In-Sentinel3" src="https://github.com/user-attachments/assets/5515fe82-8137-4123-9e70-e4cecd9fe2df" />
<img width="1916" height="904" alt="Create-Workbook-In-Sentinel4" src="https://github.com/user-attachments/assets/845a0c48-7abe-4057-b75a-d3da23caff79" />

# Step 18: Add Query to the workbook

- After opening the workbook in azure click on edit, click on add, and choose add query
- Once you create/add the query run the query and you can change the time range, visualzation, and size

<img width="1919" height="909" alt="Adding-Query-To-Workbook" src="https://github.com/user-attachments/assets/5ed1bc7d-d84f-4abd-88e1-3466e8cc2c91" />

# Step 19: Create query to log login attempts per account

- Query (Logs Logins attempts per account):

 <img width="368" height="69" alt="Query-Login-Attempts-Per-Account" src="https://github.com/user-attachments/assets/e3655124-674f-47e7-98d5-6d372397ece9" />

- Displays a table like this: 

# Step 20: Create World Attack Map In Microsoft Sentinel

<img width="778" height="172" alt="Login-Attempts-Per-Account" src="https://github.com/user-attachments/assets/673fa3da-e45f-4316-abaa-b6f46a34d6b7" />

- Query (Gather geo location data via IP):

<img width="441" height="165" alt="Query-Geo-Location-via-IP" src="https://github.com/user-attachments/assets/b07ebbb7-88ef-4f3d-84e3-d84700cceb0d" />

# Map Settings:

- Latitude: Latitude
- Longitude: Longitude
- Size by: Country
- Aggregation for location: Sum of values
- Minimum regions size: 100
- Maximum region size: 90
- Default region size: 30

# Metric Settings:

- Metric Label: Country
- Metric Value: Attempts

- After adding the query change the visualization to map to generate an image similar to this:

<img width="483" height="210" alt="Attack-Map-By-Country" src="https://github.com/user-attachments/assets/b05f94be-d10e-4911-888b-fa90e542f967" />

# IMPORTANT DO NOT FORGET

- Resources wil use free credits if they are not eliminated, and costs may start to accrue over time. Do not forget to also shutdown your virtual machine when you are done with your lab unless you plan to continue to reel in more traffic. Just keep in mind the resouces that will be allocated to keep the device running 24/7.






  
   

