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


Microsoft Azure 
O Search resources, services, and docs (G+/) 
Copilot 
... 
O 
Home > Resource Manager | Resource groups 
X 
Create a resource group 
... 
Basics 
Tags 
Review + create 
Resource group - A container that holds related resources for an Azure solution. The resource group can include all the 
resources for the solution, or only those resources that you want to manage as a group. You decide how you want to 
allocate resources to resource groups based on what makes the most sense for your organization. Learn more 
Subscription * ( 
Azure subscription 1 
Resource group name * 
RG-SOC-LAB1 
Region * O 
(US) East US 2 
Previous 
Nex 
Review + create 


