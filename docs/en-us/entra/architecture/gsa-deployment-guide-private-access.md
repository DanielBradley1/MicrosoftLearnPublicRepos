<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-private-access -->
<!-- Sitemap-Last-Modified: 2025-01-24 -->

# Microsoft Global Secure Access Deployment Guide for Microsoft Entra Private Access

[Microsoft Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access) converges network, identity, and endpoint access controls for secure access to any app or resource from any location, device, or identity. It enables and orchestrates access policy management for corporate employees. You can continuously monitor and adjust, in real time, user access to your private apps, Software-as-a-Service \(SaaS\) apps, and Microsoft endpoints. Continuous monitoring and adjusting helps you to appropriately respond to permission and risk level changes as they occur.

Microsoft Entra Private Access enables you to replace your corporate VPN. It provides your enterprise users with macro- and micro-segmented access to corporate applications that you control with Conditional Access policies. It helps you to:

- Provide Zero Trust point-to-point access to private applications with all ports and protocols. This approach prevents bad actors from lateral movement or port scans on your corporate network.
- Require multifactor authentication when users connect to private applications.
- Tunnel data over Microsoft's vast global private wide area network to maximize secure network communications.

The guidance in this article helps you to test and deploy [Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-private-access) in your production environment as you enter your deployment execution phase. [Microsoft Global Secure Access deployment guide introduction](https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-intro) provides guidance on how to initiate, plan, execute, monitor, and close your Global Secure Access deployment project.

## Identify and plan for key use cases

VPN replacement is the primary scenario for Microsoft Entra Private Access. You might have other use cases within this scenario for your deployment. For example, you might need to:

- Apply Conditional Access policies to control users and groups before they connect to private applications.
- Configure multifactor authentication as a requirement to connect to any private app.
- Enable a phased deployment that approaches Zero Trust over time for your Transmission Control Protocol \(TCP\) and User Datagram Protocol \(UDP\) -based applications.
- Use fully qualified domain name \(FQDN\) to connect to virtual networks that overlap or duplicate IP address ranges to configure access to ephemeral environments.
- Privileged Identify Management \(PIM\) to configure destination segmentation for privileged access.

After you understand the capabilities you require in your use cases, create an inventory to associate your users and groups with these capabilities. Plan to use Quick Access functionality to duplicate your VPN functionality initially so that you can test connectivity and remove your VPN. Then use Application Discovery to identify the application segments your users connect to so that you can then secure connectivity to specific IP addresses, FQDNs, and ports.

## Test and deploy Microsoft Entra Private Access

At this point, you completed the initiate and plan stages of your Secure Access Service Edge \(SASE\) deployment project. You understand what you need to implement for whom. You defined the users to enable in each wave. You have a schedule for each wave's deployment. You have met [licensing requirements](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access#licensing-overview). You're ready to enable Microsoft Entra Private Access.

1. Create end user communications to set expectations and provide an escalation path.
2. Create a roll-back plan that defines the circumstances and procedures for when you remove Global Secure Access client from a user device or disable the traffic forwarding profile.
3. [Create a Microsoft Entra group](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-groups) that includes your pilot users.
4. Enable the [Microsoft Entra Private Access traffic forwarding profile](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-manage-private-access-profile) and assign your pilot group. [Assign users and groups to traffic forwarding profiles](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-manage-users-groups-assignment).
5. Provision servers or virtual machines that have line of sight access to your applications to function as connectors, providing outbound connectivity to applications for your users. Consider load balancing scenarios and capacity requirements for acceptable performance. [Configure connectors for Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-connectors) on each connector machine.
6. If you have an inventory of enterprise applications, [configure per-app access using Global Secure Access applications](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-per-app-access). If not, [configure Quick Access for Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-quick-access).
7. Communicate expectations to your pilot group.
8. Deploy the [Global Secure Access client for Windows](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-install-windows-client) on devices for your pilot group to test.
9. Create [Conditional Access policies](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-per-app-access#assign-conditional-access-policies) per your security requirements to apply to your pilot group when these users connect to your published Global Secure Access Enterprise applications.
10. Have your pilot users test your configuration.
11. If needed, update your configuration and retest. If needed, initiate roll-back plan.
12. As needed, iterate changes to your end user communications and deployment plan.

## Configure per-app access

To maximize the value of your Microsoft Entra Private Access deployment, you should transition from Quick Access to per-app access. You can use [Application Discovery](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-application-discovery) feature to quickly create Global Secure Access applications from app segments your users access. You can also use [Global Secure Access Enterprise applications](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-per-app-access) to do create them manually, or you can use [PowerShell](https://learn.microsoft.com/en-us/entra/architecture/gsa-poc-private-access#use-powershell-to-manage-microsoft-entra-private-access) to automate creation.

1. Create the application and scope it to either all users assigned to Quick Access \(recommended\) or all users that need to access the specific application.
2. Add at least one app segment to the application. You don't need to add all app segments at the same time. You might prefer to add them slowly so that you can validate traffic flow for each segment.
3. Notice that traffic to these app segments no longer appears in Quick Access. Use Quick Access to identify app segments that you need to configure as Global Secure Access applications.
4. Continue to create Global Secure Access applications until no app segments appear in Quick Access.
5. Disable Quick Access.

After your pilot is complete, you should have a repeatable process and understand how to proceed with each wave of users in your production deployment.

1. Identify the groups that contain your wave of users.
2. Notify your support team of the scheduled wave and its included users.
3. Send planned and prepared end user communications.
4. Assign the groups to the Microsoft Entra Private Access traffic forwarding profile.
5. Deploy the Global Secure Access Client on devices for the wave's users.
6. If needed, deploy more private network connectors and create more Global Secure Access Enterprise applications.
7. If needed, create Conditional Access policies to apply to the wave's users when they connect to these applications.
8. Update your configuration. Test again to address issues, If needed, initiate roll-back plan.
9. As needed, iterate changes to your end user communications and deployment plan.

## Next steps

- Learn how to accelerate your transition to a Zero Trust security model with [Microsoft Entra Suite and Microsoft's unified security operations platform](https://www.microsoft.com/en-us/security/blog/2024/07/11/simplified-zero-trust-security-with-the-microsoft-entra-suite-and-unified-security-operations-platform-now-generally-available/)
- [Introduction to Microsoft Global Secure Access Deployment Guide](https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-intro)
- [Microsoft Global Secure Access deployment guide for Microsoft Traffic](https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-microsoft-traffic)
- [Microsoft Global Secure Access Deployment Guide for Microsoft Entra Internet Access](https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-internet-access)
- [Simulate remote network connectivity using Azure Virtual Network Gateway - Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-simulate-remote-network)
- [Simulate remote network connectivity using Azure vWAN - Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-create-remote-network-vwan)
- [Introduction to Global Secure Access Proof of Concept Guidance](https://learn.microsoft.com/en-us/entra/architecture/gsa-poc-guidance-intro)
- [Global Secure Access Proof of Concept Guidance - Configure Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/architecture/gsa-poc-private-access)
- [Global Secure Access Proof of Concept Guidance - Configure Microsoft Entra Internet Access](https://learn.microsoft.com/en-us/entra/architecture/gsa-poc-internet-access)
