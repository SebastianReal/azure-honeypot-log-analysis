# Project Summary: Azure Honeypot + Microsoft Sentinel Log Analysis

## Objective

The goal of this project was to simulate a real-world security threat scenario by deploying an intentionally vulnerable virtual machine (VM) in Microsoft Azure. The VM was exposed to the internet to attract unauthorized access attempts, which were logged, analyzed using Kusto Query Language (KQL), and visualized through Microsoft Sentinel.

## Infrastructure & Setup

- **Resource Group**: Created to logically contain all assets.
- **Virtual Network & Subnet**: Provided network segmentation for the VM.
- **Virtual Machine (Windows)**: Configured with a public IP address and inbound rules allowing all traffic.
- **Network Security Group (NSG)**: Inbound rules were modified to allow any protocol from any source, effectively exposing the VM.
- **Firewall Disabled**: On the VM to increase the likelihood of successful scanning and brute-force attempts.
- **Remote Desktop (RDP)**: Used for administrative access and configuration.

## Integration with Sentinel

- **Log Analytics Workspace**: Created and linked to the VM using the Azure Monitoring Agent.
- **Microsoft Sentinel**: Enabled on the workspace to ingest and visualize logs.
- **Watchlists**: A GeoIP CSV file was uploaded to a Watchlist to enrich event logs with geographic data.
- **Event Collection**: Focused on Security Event ID `4625` (failed login attempts).

## KQL Log Analysis

Advanced log queries were written to:
- Filter and analyze failed RDP login attempts
- Join data with the `geoip` Watchlist to identify attacker locations
- Summarize and project fields like `IpAddress`, `latitude`, `longitude`, `cityname`, and `countryname`


## Visualization

A custom Sentinel Workbook was created using a map visualization component. The enriched log data was plotted on a world map, highlighting regions generating the most failed login attempts.

- **Map Type**: Heatmap
- **Metric**: `FailureCount` per IP/location
- **Legend**: Custom labels for city and country

## Results

After 24+ hours of uptime:
- Multiple failed login attempts were logged from global IPs
- Enrichment using Watchlists enabled geospatial insights
- Visual output clearly showed high-risk sources by region

This project demonstrates:
- Experience in Azure infrastructure deployment
- Real-world understanding of threat simulation
- Skill in log analysis and KQL scripting
- Visualization of cyber threats for operational visibility
