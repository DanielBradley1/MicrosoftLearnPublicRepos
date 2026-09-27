<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/apps/plan-design/prerequisites-deploy-user-available-apps -->
<!-- Sitemap-Last-Modified: 2023-11-07 -->

# Prerequisites to deploy user-available apps

*Applies to: Configuration Manager \(current branch\)*

When you deploy applications as **Available** to user collections, then users can browse Software Center and install the apps they need.

For on-premises domain-joined clients, Software Center uses the user's domain credentials to get the list of available applications from the management point.

There are other requirements for clients that are internet-based, joined to Microsoft Entra ID, or both.

## Microsoft Entra joined devices

If you deploy applications as available to users, they can browse and install them through Software Center on Microsoft Entra devices. Configure the following prerequisites to enable this scenario:

- Enable HTTPS on the management point or enable Enhanced HTTP on the site.
- Integrate the site with [Microsoft Entra ID](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/azure-services-wizard) for **Cloud Management**.

  - Configure [Microsoft Entra user Discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configure-discovery-methods#azureaadisc).

- Deploy an application as available to a collection of users from Microsoft Entra ID.
- Enable the client setting **Use new Software Center** in the [Computer agent](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-settings#computer-agent) group.
- The client OS must be Windows 10 or later, and joined to Microsoft Entra ID. Either as purely cloud domain-joined, or Microsoft Entra hybrid joined.
- To support internet-based clients:

  - Deploy a [cloud management gateway](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/overview) \(CMG\).
  - Distribute any application content to a content-enabled CMG.
  - Enable the client setting: **Enable user policy requests from Internet clients** in the [Client Policy](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-settings#client-policy) group.

- To support clients on the intranet:

  - Add the content-enabled CMG to a boundary group used by the clients.
  - Clients must resolve the fully qualified domain name \(FQDN\) of the management point.


  Note


  For a client detected as on the intranet, but communicating via the cloud management gateway \(CMG\), it uses Microsoft Entra identity for devices joined to Microsoft Entra ID. These devices can be cloud-joined or hybrid-joined.

## Internet-based domain-joined devices

An internet-based, domain-joined device that isn't joined to Microsoft Entra ID and communicates via a cloud management gateway \(CMG\) can get apps deployed as available. The Active Directory domain user of the device needs a matching Microsoft Entra identity. When the user starts Software Center, Windows prompts them to enter their Microsoft Entra credentials. They can then see any available apps.

Configure the following prerequisites to enable this functionality:

- Windows 10 or later device, and:

  - Joined to your on-premises Active Directory domain.
  - Can communicate via [CMG](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway).

- The site has discovered the user by *both* [Active Directory](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser) and [Microsoft Entra user discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc).

Note

If you apply a [software restriction policy](https://learn.microsoft.com/en-us/windows-server/identity/software-restriction-policies/administer-software-restriction-policies) to the device, it can block the authentication prompt in Windows. Review any domain or local group policies that you apply to the device. Then remove any that might interfere with this Software Center behavior.

## Next steps

[Deploy applications](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/deploy-applications)
