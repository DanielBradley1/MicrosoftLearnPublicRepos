<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-internet-access -->
<!-- Sitemap-Last-Modified: 2025-01-24 -->

# Microsoft Global Secure Access Deployment Guide for Microsoft Entra Internet Access

[Microsoft Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access) converges network, identity, and endpoint access controls for secure access to any app or resource from any location, device, or identity. It enables and orchestrates access policy management for corporate employees. You can continuously monitor and adjust, in real time, user access to your private apps, Software-as-a-Service \(SaaS\) apps, and Microsoft endpoints. This solution helps you to appropriately respond to permission and risk level changes as they occur.

With Microsoft Entra Internet Access, you can control and manage internet access for enterprise users with managed devices when they work locally or remotely. It helps you to:

- Protect your enterprise users and managed devices from malicious internet traffic and malware infection.
- Stop users from accessing sites based on web category or fully qualified domain name.
- Collect internet usage data for reports and support investigations.

The guidance in this article helps you to test and deploy [Microsoft Entra Internet Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-internet-access) in your production environment. [Microsoft Global Secure Access deployment guide introduction](https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-intro) provides guidance on how to initiate, plan, execute, monitor, and close your Global Secure Access deployment project.

## Identify and plan for key use cases

Before you enable Microsoft Entra Internet Access, plan for what you want it to do for you. Understand use cases, such as the following, to decide which features to deploy.

- Define a baseline policy that applies to all internet access traffic routed through the service.
- Prevent specific users and groups from using managed devices to access websites by category \(such as Alcohol and Tobacco or Social Media\). Microsoft Entra Internet Access provides more than 60 categories from which you can choose.
- Prevent users and groups from using managed devices to access specific fully qualified domain names \(FQDN\).
- Configure override policies to allow groups of users to access sites that your web filtering rules would otherwise block.
- Extend the capabilities of Microsoft Entra Internet Access to entire networks, including devices that are not running the Global Secure Access client

  - [Simulate remote network connectivity using a remote virtual wide-area network \(vWAN\)](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-create-remote-network-vwan)
  - [Simulate remote network connectivity using an Azure virtual network gateway \(VNG\)](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-simulate-remote-network)

After you understand the capabilities you require in your use cases, create an inventory to associate your users and groups with these capabilities. Understand which users and groups to block or allow access to which web categories and FQDNs. Include rule prioritization for each user group.

## Test and deploy Microsoft Entra Internet Access

At this point, you completed initiate and plan stages of your Secure Access Services Edge \(SASE\) deployment project. You understand what you need to implement for whom. You defined which users to enable in each wave. You have a schedule for each wave's deployment. You have met [licensing requirements](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access#licensing-overview). You're ready to enable Microsoft Entra Internet Access.

1. Complete the Global Secure Access [prerequisites](https://learn.microsoft.com/en-us/entra/global-secure-access/quickstart-access-admin-center#prerequisites).
2. [Create a Microsoft Entra group](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-groups) that includes your pilot users.
3. Enable the Microsoft Entra Internet access and Microsoft traffic forwarding profiles. Assign your pilot group to each profile.

Note

Microsoft traffic is a subset of internet traffic that has its own dedicated tunnel gateway. For optimal performance, enable Microsoft Traffic with Internet access traffic profile.

1. Create end user communications to set expectations and provide an escalation path.
2. Create a roll-back plan that defines the circumstances and procedures for when you remove Global Secure Access client from a user device or disable the traffic forwarding profile.
3. Send end user communications.
4. Deploy the [Global Secure Access client for Windows](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-install-windows-client) on devices for your pilot group to test.
5. Configure remote networks using [vWAN](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-create-remote-network-vwan) or [VNG](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-simulate-remote-network) if in scope.
6. Configure [web content filtering policies](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-web-content-filtering#create-a-web-content-filtering-policy) to allow or block categories or FQDNs based on the use cases that you defined during planning.

   - Block by category: define a rule that blocks one of many predefined, managed categories
   - Block by FQDN: define a rule that blocks an FQDN that you specify
   - Override: define a rule that allows a web category or FQDN that you specify

7. Create [security profiles](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-web-content-filtering#create-a-security-profile) that group and prioritize your web content filtering policies based on your plan.

   - Baseline profile: use Baseline profile feature to group web content filtering policies that apply to all users by default.
   - Security profiles: create security profiles to group web content filtering policies that apply to a subset of users.

8. Create and link [Conditional Access policies](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-web-content-filtering#create-and-link-conditional-access-policy) to apply your security profiles to your pilot group. The default Baseline profile doesn't require a Conditional Access policy.
9. Have your pilot users test your configuration.
10. Confirm activity in the [Global Secure Access Traffic logs](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-view-traffic-logs).
11. Update your configuration to address any issues and repeat the test. Use roll-back plan if needed.
12. As needed, iterate changes to your end user communications and deployment plan.

After your pilot is complete, you have a repeatable process to understand how to proceed with each wave of users in your production deployment.

1. Identify the groups that contain your wave of users.
2. Notify the support team of the scheduled wave and its included users.
3. Send prepared end user communications according to your plan.
4. Assign the groups to the Microsoft Entra Internet Access traffic forwarding profile.
5. Deploy the Global Secure Access Client on the devices the users in this wave.
6. If needed, create and configure more web content filtering policies to allow or block categories or FQDNs based on the use cases that you defined in your plan.
7. If needed, create more security profiles that group and prioritize your web content filtering policies based on your plan.
8. Create Conditional Access policies to apply new security profiles to the relevant groups in this wave or add the new groups of users to existing Conditional Access policies for existing security profiles.
9. Update your configuration. Test again to address issues. If needed, initiate roll-back plan.
10. As needed, iterate changes in your end user communications and deployment plan.

## Next steps

- Learn how to accelerate your transition to a Zero Trust security model with [Microsoft Entra Suite and Microsoft's unified security operations platform](https://www.microsoft.com/en-us/security/blog/2024/07/11/simplified-zero-trust-security-with-the-microsoft-entra-suite-and-unified-security-operations-platform-now-generally-available/)
- [Introduction to Microsoft Global Secure Access Deployment Guide](https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-intro)
- [Microsoft Global Secure Access Deployment Guide for Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-private-access)
- [Microsoft Global Secure Access deployment guide for Microsoft Traffic](https://learn.microsoft.com/en-us/entra/architecture/gsa-deployment-guide-microsoft-traffic)
- [Simulate remote network connectivity using Azure Virtual Network Gateway - Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-simulate-remote-network)
- [Simulate remote network connectivity using Azure vWAN - Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-create-remote-network-vwan)
- [Introduction to Global Secure Access Proof of Concept Guidance](https://learn.microsoft.com/en-us/entra/architecture/gsa-poc-guidance-intro)
- [Global Secure Access Proof of Concept Guidance - Configure Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/architecture/gsa-poc-private-access)
- [Global Secure Access Proof of Concept Guidance - Configure Microsoft Entra Internet Access](https://learn.microsoft.com/en-us/entra/architecture/gsa-poc-internet-access)
