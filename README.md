# Azure Sentinel (SIEM) Honeypot Home Lab

<img width="358" height="198" alt="image" src="https://github.com/user-attachments/assets/1b3be7ab-5057-491b-a6ca-2d4f819138a7" />

# Project Summary 

Build an Azure-based honeypot environment inspired by Josh Madakor’s lab to simulate real-world attack traffic. Collected and ingested SecurityEvent logs into Azure Log Analytics and Microsoft Sentinel. Developed custom KQL queries to detect failed logins, brute-force activity, and geolocation-based attack patterns. Design and implement a SOC-style dashboard to visualize attacker IPs, geographic distribution, and authentication trends.

# Description

In this homelab we will go through the steps to creating a Azure Sentinel Honeypot to be able to ingest real-time data for creating useful analytical dashboards. Going step by step on setting up the entire environment. 

 
# Learning Objectives 

Azure Honeypot with Microsoft Sentinel – Attack Detection &amp; Visualization Dashboard

- Created a resource group, virtual machine and a virtual network
- I had to configure the Network Security Group (NSG) and allow ANY inbound connections 
- RDP into the VM I had created and turned off the firewall
- Verified the VM was accessible from my personal device by pinging the public IP assigned to the VM
- Created a Log Analytics Workspace, connected it to Microsoft Sentinel, configured the connector for "Windows Security Events via AMA", 
- Created Data collection rule in Microsoft Sentinel
- Enriched data by geolocation which in turn helped create the visual dashboards!

Overview: 

# Step 1: Create a Resource Group

- Name your resource group, click review + create 

 <img width="1076" height="1754" alt="Creating-Resource-Group" src="https://github.com/user-attachments/assets/100d1134-4cee-438d-8a8d-1d219c37f48e" />

 # Step 2: Create Virtual Network

<img width="1079" height="1753" alt="Creating-Virtual-Network" src="https://github.com/user-attachments/assets/fa0314be-d9b9-4d26-90b6-d34dd49b16cd" />
<img width="1078" height="1708" alt="Creating-Virtual-Network2" src="https://github.com/user-attachments/assets/bbc8cf41-6436-445e-9e4c-deddfd1a72f2" />
<img width="1075" height="1754" alt="Creating-Virtual-Network3" src="https://github.com/user-attachments/assets/55ce932b-e874-40ff-a4af-74d9414590ec" />
<img width="1078" height="1711" alt="Creating-Virtual-Network4" src="https://github.com/user-attachments/assets/577abb0d-42b1-42ec-bc52-b6fb223f491a" />





