# Azure Honeypot + Microsoft Sentinel Log Analysis

This project demonstrates how to deploy an intentionally vulnerable virtual machine (honeypot) in Azure to collect global attack data, analyze it with Kusto Query Language (KQL), and visualize it on a world map using Microsoft Sentinel.

## Objectives

- Deploy a honeypot virtual machine to attract real-world attack attempts
- Configure Azure Sentinel and Log Analytics Workspace
- Analyze failed login attempts with KQL
- Visualize attacker IP geolocation data in Sentinel workbooks

## Tools & Technologies

- Microsoft Azure
- Microsoft Sentinel
- Kusto Query Language (KQL)
- Log Analytics Workspace
- Network Security Groups (NSGs)

## Project Overview

1. **Deploy Azure Resources:** Resource Group, VNet, and VM
2. **Expose VM to Public Internet:** Modify NSG to allow all inbound traffic
3. **Disable Firewall:** To increase exposure to threats
4. **Link VM to Log Analytics Workspace:** Via Azure Monitoring Agent
5. **Use Sentinel Watchlists:** Enrich logs with geolocation data
6. **Visualize Attack Data:** With a custom workbook showing map view
