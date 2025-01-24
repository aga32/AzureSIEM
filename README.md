# AzureSIEM
Setting up Azure Sentinel and a cloud-based honeypot VM to monitor, log, and map failed login attempts and attack origins from global IP addresses on a world map.

I have never worked with cloud-based systems before so I decided to take a shot at this project! I set up Azure Sentinel, a cloud-based SIEM, along with a deliberately vulnerable Virtual Machine in the cloud, which acts as a honeypot to attract and log attacks from global IP addresses. By disabling the VM’s external and internal firewalls, I allowed attackers to target it, collecting failed login data in the process. Using a PowerShell script, I extracted the attacker's IPs and sent them to a geolocation API to retrieve details like country, state, and coordinates. This data was logged into Azure Sentinel, where I visualized the attack origins on a world map to gain insights into global threat activity.

The resources I followed to complete this project are as followed:

https://cyberspikes.com/projects/setting-up-a-siem-in-azure/

https://www.youtube.com/watch?v=tHicENradv8

https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1


