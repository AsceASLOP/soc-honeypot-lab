# soc-honeypot-lab
Azure Honeypot with Microsoft Sentinel – Attack Detection &amp; Visualization Dashboard

- Created a resource group, virtual machine and a virtual network
- I had to configure the Network Security Group (NSG) and allow ANY inbound connections 
- RDP into the VM I had created and turned off the firewall
- Verified the VM was accessible from my personal device by pinging the public IP assigned to the VM
- Created a Log Analytics Workspace, connected it to Microsoft Sentinel, configured the connector for "Windows Security Events via AMA", 
- Created Data collection rule in Microsoft Sentinel
- Enriched data by geolocation which in turn helped create the visual dashboards!

