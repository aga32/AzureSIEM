# AzureSIEM
Setting up Azure Sentinel and a cloud-based honeypot VM to monitor, log, and map failed login attempts and attack origins from global IP addresses on a world map.

I have never worked with cloud-based systems before so I decided to take a shot at this project! I set up Azure Sentinel, a cloud-based SIEM, along with a deliberately vulnerable Virtual Machine in the cloud, which acts as a honeypot to attract and log attacks from global IP addresses. By disabling the VM’s external and internal firewalls, I allowed attackers to target it, collecting failed login data in the process. Using a PowerShell script, I extracted the attacker's IPs and sent them to a geolocation API to retrieve details like country, state, and coordinates. This data was logged into Azure Sentinel, where I visualized the attack origins on a world map to gain insights into global threat activity.

The resources I used to complete this project are as follows:

https://cyberspikes.com/projects/setting-up-a-siem-in-azure/

https://www.youtube.com/watch?v=tHicENradv8

https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1

Activity after implementation:
![image](https://github.com/user-attachments/assets/12775866-900d-4220-bb80-a91c75f5b226)

Activity ~ 4 hours after implementation:
![image](https://github.com/user-attachments/assets/bf10d674-f690-4415-b76f-7ae15605f1de)

# Issues I had while working on this project

Overall, this project was straightforward and relatively easy to follow. Once I became familiar with the Azure platform, completing the steps became much simpler. However, I encountered an issue with differences in the Azure platform compared to the original documentation I was following, which was a few years old. Specifically, I faced a challenge when extracting the raw data from the 'failed_rdp' file. It no longer supported data extraction as described in the documentation. To overcome this, I found a solution by using the query provided in the code section of this repository. This allowed me to extract only the raw data from my 'failed_rd'p file and use its key fields to plot the map successfully.

# Azure Sentinel Honeypot Setup: Steps I Completed  

1. Created an Azure Account and VM  
   I set up my Azure account, logged into the portal, and created a virtual machine with basic configurations (name, region, and login creds).  

2. Organized Resources 
   I created a resource group named `honeypot-lab` to manage all the resources related to this project.  

3. Configured Networking and Security  
   I set up a Network Security Group, added an inbound rule to allow all traffic, and ensured unrestricted public internet access to the VM.  

4. Finalized and Launched the VM  
   After reviewing the settings, I finalized the setup and successfully launched the VM.  

5. Set Up Log Analytics Workspace  
   I created a Log Analytics workspace in the `honeypot-lab` resource group and configured it to capture logs from the VM.  

6. Connected the Workspace to the VM  
   I linked the Log Analytics workspace to the VM, allowing log data to sync for analysis.  

7. Set Up Azure Sentinel  
   I configured Azure Sentinel as my SIEM platform, connected it to the Log Analytics workspace, and ensured it was ready to analyze and display attack data.  

8. Worked on the VM  
   Using Remote Desktop, I accessed the VM, disabled the firewall for full traffic visibility, and ensured it was highly discoverable.  

9. Configured Logging and Geolocation Data  
   I obtained an IPGeolocation API key, ran a PowerShell script to extract geolocation data from failed login attempts and set up custom logs in Log Analytics. (https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1) 

10. Verified Logs and Extract Raw Data
    I confirmed that logs were syncing in Log Analytics and ran a query to extract key fields from the raw data like latitude, longitude, and country from the custom logs.

12. Built an Attack Map in Sentinel  
    I used Azure Sentinel to create a world map in Workbooks, visualizing attack data by geolocation and event frequency in real time.  

13. Monitored and Cleaned Up  
    I monitored the attack patterns on the map and deleted the resource group to clean up once the project was complete.  

This project gave me hands-on experience with cloud security monitoring and using Azure Sentinel as a SIEM platform.
