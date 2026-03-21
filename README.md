# Azure Sentinel (SIEM) Honeypot Home Lab

<img width="358" height="198" alt="image" src="https://github.com/user-attachments/assets/1b3be7ab-5057-491b-a6ca-2d4f819138a7" />

# Project Summary 

Build an Azure-based honeypot environment inspired by Josh Madakor’s lab to simulate real-world attack traffic. Collected and ingested SecurityEvent logs into Azure Log Analytics and Microsoft Sentinel. Developed custom KQL queries to detect failed logins, brute-force activity, and geolocation-based attack patterns. Design and implement a SOC-style dashboard to visualize attacker IPs, geographic distribution, and authentication trends.

# Description

In this homelab we will go through the steps to creating a Azure Sentinel Honeypot to be able to ingest real-time data for creating useful analytical dashboards. Going step by step on setting up the entire environment. 

 
# Learning Objectives 

Azure Honeypot with Microsoft Sentinel – Attack Detection &amp; Visualization Dashboard

- Understand honeypot deployment in cloud environments
Configure and expose an Azure VM to simulate a vulnerable system and attract unauthorized access attempts.

- Gain hands-on experience with log ingestion and SIEM workflows
Ingest Windows Security Event logs into Azure Log Analytics and analyze them using Microsoft Sentinel.

- Develop proficiency in Kusto Query Language (KQL)
Write and optimize queries to detect authentication events, including successful and failed logins (Event IDs 4624 and 4625).

- Detect and analyze brute-force attack patterns
Identify repeated failed login attempts from single or distributed IP addresses.

- Perform geolocation enrichment of threat data
Use IP-based enrichment to map attacker origin (country, state, city) and identify attack trends.
Overview: 

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

<img width="1073" height="1712" alt="Creating-Virtual-Machine" src="https://github.com/user-attachments/assets/89d47863-4338-4d38-a1b9-8e0c7c5e5781" />
<img width="1076" height="1712" alt="Creating-Virtual-Machine2" src="https://github.com/user-attachments/assets/addde12b-a751-44b8-aaee-5560e0c1cc04" />
<img width="1077" height="1713" alt="Creating-Virtual-Machine3" src="https://github.com/user-attachments/assets/2482a053-28a6-4d87-b1c2-db9bbbd2b045" />
<img width="1077" height="1713" alt="Creating-Virtual-Machine4" src="https://github.com/user-attachments/assets/bb94cb76-4812-40fb-a9d5-97c9e07bbf2c" />

# Step 5: Check Resource Groups 

- Verify that the resources you had created within Azure are in the same region and resource group

<img width="1076" height="1749" alt="Verify-Resource-Creations" src="https://github.com/user-attachments/assets/6905a64d-4a67-4463-99cd-c1904b303ebc" />

# Step 6: Configure NSG (Network Security Group) 

- Select NSG in the resource group 
- Create an Inbound Security Rule allowing any traffic to the VM
- The rule should look like this when creating it:

<img width="1078" height="1863" alt="Configuring-NSG" src="https://github.com/user-attachments/assets/3dfcceef-f6b7-460b-8985-184d1f3bb137" />

# Step 7: Conenct to the VM via RDP

- In the resource group, if you click on the VM on the right pane it will display the public IP assigned to that VM 

<img width="1078" height="1744" alt="VM-Public-IP" src="https://github.com/user-attachments/assets/42d0d35c-6100-4325-b330-5b30a5b00475" />

# Step 8: Turn off Windows Firewall on VM 

- Once you are remoted to the VM navigate to Windows Defense Firewall with Advanced Features and click on Windows Defender Firewall properties

<img width="1076" height="781" alt="Windows-Defender-Firewall-Proprerties" src="https://github.com/user-attachments/assets/2be1ce98-36a4-4a2c-97f6-c4d6c509724d" />

- The pane that pops up will display 4 tabs: Domain Profile, Private Profile, Public Profile and IPsec Settings. Disable Domain, Private and Public Profile

<img width="403" height="461" alt="Windows-Defender-Firewall-Proprerties2" src="https://github.com/user-attachments/assets/f3cfb579-c4bc-4ee7-86e5-6ddf8b35a94b" />

# Step 9: Once the firewall on the VM has been disabled, ping your VM machine from your desktop to verify that the VM is accessible from public internet 










