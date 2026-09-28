<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-and-migration-planning?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# Network and migration planning for Microsoft 365

*This article applies to Microsoft 365 Enterprise*

This article contains links to information about network planning and testing, and migration to Microsoft 365.

Before you deploy for the first time or migrate to Microsoft 365, you can use the information in these articles to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Microsoft 365.

This article is part of [Network planning and performance tuning for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance?view=o365-worldwide).

For the steps to optimize your network for Microsoft 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://learn.microsoft.com/en-us/previous-versions/microsoft-365/solutions/cloud-architecture-models) poster.

## Estimate network bandwidth requirements

Using Microsoft 365 might increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Microsoft 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.

To estimate the bandwidth, use the following steps:

1. Assess the number of clients that will use each internet egress. Let our multi-terabit network handle as much of the connection as possible.
2. Determine which Microsoft 365 services and features will be available for clients to use. You'll likely have groups of people with different services or usage profiles.
3. Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization and the different geographic locations. You can cross-check your results against our old calculators for [Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) and [Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/prepare-network).
4. Use the measurements from the pilot group to extrapolate the entire organization's needs and retest to validate the estimations before making any changes to your network.

## Test your existing network

**Network tools.** Test and validate your internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.

- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.
- Use the [Microsoft Support and Recovery Assistant for Microsoft 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Microsoft 365 problems.
- [Microsoft 365 network connectivity test tool](https://learn.microsoft.com/en-us/microsoft-365/enterprise/office-365-network-mac-perf-onboarding-tool): Tests Microsoft 365 network connectivity.

## Best practices for network planning and improving migration performance for Microsoft 365

Dig a little deeper into these best practices for more information about improving your Microsoft 365 experience.

1. Want to get started helping your users right away? See [Best practices for using Microsoft 365 on a slow network](https://learn.microsoft.com/en-us/microsoft-365/enterprise/best-practices-for-using-office-365-on-a-slow-network?view=o365-worldwide) for tips on using Microsoft 365, including SharePoint, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Microsoft 365 experience and includes information on easy ways to customize your web pages and how to set your internet Explorer settings for the best Microsoft 365 experience.
2. Read [Microsoft 365 Network Connectivity Principles](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles?view=o365-worldwide) to understand the connectivity principles for securely managing Microsoft 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Microsoft 365 network connectivity.
3. Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Microsoft 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Microsoft 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).
4. Microsoft 365 network traffic performs best when it's treated as a trusted internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the internet with the proper Network Address Translation \(NAT\) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Microsoft 365 endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/managing-office-365-endpoints?view=o365-worldwide)for additional guidance on configuring your network to handle Microsoft 365 as a trusted internet service on your network.
5. Ensure [Managing Microsoft 365 endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/managing-office-365-endpoints?view=o365-worldwide). The additional traffic going to Microsoft 365 results in an increase of outbound proxy connections and an increase in secure traffic over TLS/SSL.
6. If your outbound proxies require user authentication you might experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Microsoft 365 domains can reduce this overhead.
7. If you have a large number of shared calendars and mailboxes, you might see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Microsoft 365 for Outlook.
8. Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see the [Networking roadmap for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/networking-roadmap-microsoft-365?view=o365-worldwide).
9. If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Microsoft 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single internet egress and enables local internet egress for Microsoft 365 destined network requests.
10. Some customers find internal network settings can affect performance. Settings such as maximum transmission unit \(MTU\) size, network autonegotiation or autodetection, and suboptimal routes to the internet are common places to look.

## Network planning reference for Microsoft 365

These articles contain detailed Microsoft 365 network reference information.

- [Managing Microsoft 365 endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/managing-office-365-endpoints?view=o365-worldwide)
- [Content delivery networks](https://learn.microsoft.com/en-us/microsoft-365/enterprise/content-delivery-networks?view=o365-worldwide)
- [External Domain Name System records for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/external-domain-name-system-records?view=o365-worldwide)
- [IPv6 support in Microsoft 365 services](https://learn.microsoft.com/en-us/microsoft-365/enterprise/ipv6-support?view=o365-worldwide)
- [Microsoft 365 Network Connectivity Principles](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles?view=o365-worldwide)
- [Plan for network devices that connect to Microsoft 365 services](https://learn.microsoft.com/en-us/microsoft-365/enterprise/plan-for-network-devices?view=o365-worldwide)
- [Setup guides for Microsoft 365 services](https://learn.microsoft.com/en-us/microsoft-365/enterprise/setup-guides-for-microsoft-365?view=o365-worldwide)

## Related content

[Microsoft 365 Enterprise overview](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-overview?view=o365-worldwide)
