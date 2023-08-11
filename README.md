# CREATED a SOC: CYBER ATTACK TRAFFIC GENERATION 
![image](https://github.com/Osagieoshodi/Azure-Honeynet-SOC/assets/141954663/de41bd4f-67ca-48f5-ad5e-a0462a832819)



## Introduction

For this project, I created a small honeynet in Azure. I gathered logs from different sources and stored them in a Log Analytics workspace. Microsoft Sentinel used these logs to make attack maps, send alerts, and handle incidents. Initially, I recorded security data in an unsafe setup for a day, improved security with controls, recorded data for another day, and now present the findings below. The metrics we'll display include:

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)

## Architecture Before Hardening / Security Controls
![image](https://github.com/Osagieoshodi/Azure-Honeynet-SOC/assets/141954663/dccfefb0-dd42-4872-94dd-861e945144b2)


## Architecture After Hardening / Security Controls
![image](https://github.com/Osagieoshodi/Azure-Honeynet-SOC/assets/141954663/cfa43bf6-9106-4395-9111-2d2d5bb3b328)


The architecture of the mini honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

In the "BEFORE" metrics, all the tools were initially set up and made accessible on the internet. The Virtual Machines were open to all network security settings and had their internal firewalls disabled. All other tools were set up with public access points that could be seen from the internet, meaning there was no need for Private Endpoints.

In the "AFTER" metrics, the Network Security Groups were made more secure by blocking ALL traffic except for connections from my admin workstation. Additionally, the other tools had their internal firewalls activated and were safeguarded by Private Endpoints.


## Attack Maps Before Hardening / Security Controls
![image](https://github.com/Osagieoshodi/Azure-Honeynet-SOC/assets/141954663/ea052188-4f42-4e2b-997a-0058d6864982)
![image](https://github.com/Osagieoshodi/Azure-Honeynet-SOC/assets/141954663/365d403f-2d18-4f60-aed3-efca999d24db)
![image](https://github.com/Osagieoshodi/Azure-Honeynet-SOC/assets/141954663/188c4147-45e1-42bf-ab7d-76278e20bee8)

## Attack Maps After Hardening / Security Controls
![image](https://github.com/Osagieoshodi/Azure-Honeynet-SOC/assets/141954663/0df99159-8055-4ef7-9c11-023abe9375b4)
![image](https://github.com/Osagieoshodi/Azure-Honeynet-SOC/assets/141954663/1d1be4fb-f0c7-47cc-8a88-2151bffd3e78)
![image](https://github.com/Osagieoshodi/Azure-Honeynet-SOC/assets/141954663/ec2c63f5-d495-4176-b35c-0acc7a221a21)







## Metrics Before Hardening / Security Controls

Below is a table displaying the metrics we measured in our insecure environment for 24 hours:
Start Time 2023-07-31T05:05:30.5009022Z
Stop Time 2023-08-01T05:05:30.5009022Z

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 27435
| Syslog                   | 2478
| SecurityAlert            | 7
| SecurityIncident         | 208
| AzureNetworkAnalytics_CL | 1840

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

Below is a table displaying the metrics we recorded within our setting for an additional 24-hour period, subsequent to implementing security measures:
Start Time 2023-08-07T07:43:59.2702654Z
Stop Time	2023-08-08T07:43:59.2702654Z

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 8989
| Syslog                   | 1
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

## Conclusion

In this project, I set up a small, simulated network (honeynet) in Microsoft Azure. I connected different sources of logs to a central place called Log Analytics. To help me identify and respond to potential issues, I used a tool called Microsoft Sentinel. It would send alerts and create records of incidents based on the logs collected. I wanted to see how effective the security measures were, I measured certain indicators of the network's vulnerability before and after adding security controls. The interesting thing is that I noticed a significant drop in the number of security problems and incidents after putting those security measures in place. This really showed the security efforts so far were working.
It's important to mention that if I was still using the network overly during the first 24 hours after adding security measures, I might have seen more security issues and alerts during that time.
