<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-network -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 3: Secure and configure your network

After you configured your admin settings in the Security Center, you're ready to secure and configure your network. This article covers some key network requirements and recommendations to ensure optimal connectivity and performance for your tenant.

## Internet connection

Recommendations for your internet connection include:

- Use a reliable and high-speed internet connection.
- Minimize round-trip time \(RTT\) from your network to the Microsoft global network.

## Network design

Recommendations for your network design include:

- Simplify your network design to avoid hair-pinning or centralizing traffic to specific locations.
- Ensure direct and efficient routing to Microsoft data centers.

Use the measurements from the pilot group to extrapolate the entire organization's needs and retest to validate the estimations before making any changes to your network.

## Network planning and assessment

- **Bandwidth Requirements:** [Estimate the bandwidth needed for your organization by considering the number of users, types of applications used, and peak usage times.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance)
- **Network Assessment Tools:** [Use tools like the Microsoft 365 Network Connectivity Test to evaluate your current network performance and identify potential bottlenecks.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance)

The following links provide reference information for network planning and optimization:

| Category | Description |
| --- | --- |
| **Network Planning** | Want fast connections and pages that load quickly? Read [Getting the best connectivity and performance in Microsoft 365.](https://aka.ms/o365perfprinciples). Read [Microsoft 365 Network Connectivity Overview](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-networking-overview) to understand concepts. |
| **Measuring your network** | Read [Microsoft 365 performance tuning using baselines and performance history](https://learn.microsoft.com/en-us/microsoft-365/enterprise/performance-tuning-using-baselines-and-history) and [Performance troubleshooting plan for Microsoft 365.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/performance-troubleshooting-plan) Use these tools to [evaluate your existing network.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-and-migration-planning#calculators) |
| **Best practices** | [Best practices for network planning and improving migration performance](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-and-migration-planning#BestPractices) for Microsoft 365. Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network.](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) [Microsoft 365 Network Connectivity Principles](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles) helps you understand the most recent guidance for securely optimizing Microsoft 365 network connectivity. |
| **Reference** | Want the details, like a list of IP addresses and ports? See the [Network planning reference for Microsoft 365.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-and-migration-planning#NetReference) |
| **Optimization** | For the steps to optimize your network for Microsoft 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects poster.](https://learn.microsoft.com/en-us/microsoft-365/solutions/cloud-architecture-models) |

## Network configuration

- **Local Egress:** [Allow Microsoft 365 traffic to exit the network locally at each branch office to reduce latency and improve performance.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-networking-overview)
- **Bypass Proxies and Inspection Devices:** [Configure your network to bypass proxies and packet inspection devices for Microsoft 365 traffic to avoid unnecessary delays.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-networking-overview)

## Optimizing specific services

- **Exchange Online:** [Fine-tune settings for Exchange Online to ensure optimal email performance. This includes configuring client access and optimizing mailbox settings.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance)
- **Microsoft Teams:** [Ensure your network can handle real-time communication by prioritizing Teams traffic and optimizing settings for audio and video quality.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance)
- **SharePoint and OneDrive:** [Optimize file access and sharing by configuring caching and sync settings appropriately.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance)

## Monitoring and troubleshooting

- **Performance Monitoring:** [Regularly monitor network performance using tools like Microsoft 365 Admin Center and third-party network monitoring solutions.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance)
- **Troubleshooting:** [Develop a performance troubleshooting plan to quickly identify and resolve issues as they arise.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance)

## Security considerations

- **Firewall Rules:** [Ensure that your firewall rules are configured to allow Microsoft 365 traffic without unnecessary restrictions.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)
- **Network Segmentation:** [Segment your network to isolate critical Microsoft 365 services and protect them from potential threats.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)

## Endpoints and IP ranges

Configure your network to allow traffic to [Microsoft 365 URLs and IP address ranges.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges) Regularly update your firewall and proxy settings to accommodate changes in Microsoft 365 endpoints.

To configure endpoint and IP ranges:

1. Manage [Microsoft 365 endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/managing-office-365-endpoints) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated as needed at the beginning of each month, with new IP addresses and URLs published 30 days in advance of being active.
2. Refer to the following resources to view IP address ranges:

   - [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges#exchange-online)
   - [Sharepoint Online and OneDrive](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business)
   - [Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges#microsoft-teams)
   - [Microsoft 365 Common and Office Online](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)

## Performance tuning

Monitor network performance and make adjustments as needed to maintain optimal service levels:

- [Tune Office 365 performance.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/tune-microsoft-365-performance) For information about using network address translation with Office 365, see [NAT support with Office 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/nat-support-with-microsoft-365).
- [Tune Exchange Online performance.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/tune-exchange-online-performance)
- [Prepare your organization's network for Microsoft Teams.](https://learn.microsoft.com/en-us/microsoftteams/prepare-network)
- [Tune SharePoint performance.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/tune-sharepoint-online-performance)

For more information, see [Performance tuning and troubleshooting resources for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance#performance-tuning-and-troubleshooting-resources-for-microsoft-365)

Note

For education scenarios:

- Considerations for performance tuning will be based on your usage scenarios. Microsoft education solutions uses Exchange, OneDrive, SharePoint, and Microsoft Teams services.

## Next steps

Next, you're ready to sync your on-premises Active Directory.

[Next: Sync your on-premises Active Directory>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-sync-on-premises-ad)
