<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/enhanced-http -->
<!-- Sitemap-Last-Modified: 2023-11-16 -->

# Enhanced HTTP

*Applies to: Configuration Manager \(current branch\)*

Microsoft recommends using HTTPS communication for all Configuration Manager communication paths, but it's challenging for some customers because of the overhead of managing PKI certificates. With enhanced HTTP, Configuration Manager can provide secure communication by issuing self-signed certificates to specific site systems.

There are two primary goals for this configuration:

- You can secure sensitive client communication without the need for PKI server authentication certificates.
- Clients can securely access content from distribution points without the need for a network access account, client PKI certificate, or Windows authentication.

All other client communication is over HTTP. Enhanced HTTP isn't the same as enabling HTTPS for client communication or a site system.

Note

PKI certificates are still a valid option for customers with the following requirements:

- All client communication is over HTTPS
- Advanced control of the signing infrastructure

If you're already using PKI, site systems use the PKI certificate bound in IIS even if you enable enhanced HTTP.

## Scenarios

The following scenarios benefit from enhanced HTTP:

### Scenario 1: Client to management point

[Microsoft Entra joined devices](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-azure-ad-join) and devices with a [Configuration Manager issued token](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-cmg-token) can communicate with a management point configured for HTTP if you enable enhanced HTTP for the site. With enhanced HTTP enabled, the site server generates a certificate for the management point allowing it to communicate via a secure channel.

Note

This scenario doesn't require using an HTTPS-enabled management point, but it's supported as an alternative to using enhanced HTTP. For more information on using an HTTPS-enabled management point, see [Enable management point for HTTPS](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-authentication#enable-management-point-for-https).

### Scenario 2: Client to distribution point

A workgroup or Microsoft Entra joined client can authenticate and download content over a secure channel from a distribution point configured for HTTP. These types of devices can also authenticate and download content from a distribution point configured for HTTPS without requiring a PKI certificate on the client. It's challenging to add a client authentication certificate to a workgroup or Microsoft Entra joined client.

This behavior includes OS deployment scenarios with a task sequence running from boot media, PXE, or Software Center. For more information, see [Network access account](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/accounts#network-access-account).

### Scenario 3: Microsoft Entra device identity

A Microsoft Entra joined or [hybrid Microsoft Entra device](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-azure-ad-join-hybrid) without a Microsoft Entra user signed in can securely communicate with its assigned site. The cloud-based device identity is now sufficient to authenticate with the CMG and management point for device-centric scenarios. \(A user token is still required for user-centric scenarios.\)

## Features

The following Configuration Manager features support or require enhanced HTTP:

- [Cloud management gateway](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/overview)
- [OS deployment without a network access account](https://learn.microsoft.com/en-us/intune/configmgr/osd/plan-design/planning-considerations-for-automating-tasks#enhanced-http)
- [Enable co-management for new internet-based Windows devices](https://learn.microsoft.com/en-us/intune/configmgr/comanage/tutorial-co-manage-new-devices)
- [App approvals via email](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/app-approval#bkmk_email-approve)
- [Administration service](https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/overview)
- [View recently connected consoles](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console#bkmk_viewconnected)
- [BitLocker management key recovery](https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/bitlocker-management#prerequisites-for-the-recovery-service) \(version 2103 and later\)
- [Software Center](https://learn.microsoft.com/en-us/intune/configmgr/apps/plan-design/plan-for-software-center#support-for-enhanced-http) user-available applications \(version 2107 and later\)
- [Company Portal on co-managed devices](https://learn.microsoft.com/en-us/intune/configmgr/comanage/company-portal) \(version 2107 and later\)

Note

The software update point and related scenarios have always supported secure HTTP traffic with clients as well as the cloud management gateway. It uses a mechanism with the management point that's different from certificate- or token-based authentication.

## Unsupported scenarios

Enhanced HTTP doesn't currently secure all communication in Configuration Manager. The following list summarizes some key functionality that's still HTTP.

- Client peer-to-peer communication for content
- State migration point
- Remote tools
- Reporting services point

Note

This list isn't exhaustive.

## Prerequisites

- A management point configured for HTTP client connections. Set this option on the **General** tab of the management point role properties.
- A distribution point configured for HTTP client connections. Set this option on the **Communication** tab of the distribution point role properties. Don't enable the option to **Allow clients to connect anonymously**.
- For scenarios that require Microsoft Entra authentication, [onboard the site](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-azure-ad) to Microsoft Entra ID for cloud management. If you don't onboard the site to Microsoft Entra ID, you can still enable enhanced HTTP.
- *For [Scenario 3](#scenario-3-azure-ad-device-identity) only*: A client running a supported version of Windows 10 or later and joined to Microsoft Entra ID. The client requires this configuration for Microsoft Entra device authentication.

Note

There are no OS version requirements, other than what the [Configuration Manager client supports](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).

## Configure the site

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node. Select the site and choose **Properties** in the ribbon.
2. Switch to the **Communication Security** tab. Select the option for **HTTPS or HTTP**. Then enable the option to **Use Configuration Manager-generated certificates for HTTP site systems**.

Tip

Wait up to 30 minutes for the management point to receive and configure the new certificate from the site.

You can also enable enhanced HTTP for the central administration site \(CAS\). Use this same process, and open the properties of the CAS. This action only enables enhanced HTTP for the SMS Provider role at the CAS. It's not a global setting that applies to all sites in the hierarchy.

For more information on how the client communicates with the management point and distribution point with this configuration, see [Communications from clients to site systems and services](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/communications-between-endpoints#Planning_Client_to_Site_System).

## Validate the certificate

You can see these certificates in the Configuration Manager console. Go to the **Administration** workspace, expand **Security**, and select the **Certificates** node. Look for the **SMS Issuing** root certificate and the site server role certificates issued by the SMS Issuing root.

When you enable enhanced HTTP, the site server generates a self-signed certificate named **SMS Role SSL Certificate**. This certificate is issued by the root **SMS Issuing** certificate. The management point adds this certificate to the IIS default web site bound to port 443.

To see the status of the configuration, review **mpcontrol.log**.

## Conceptual diagram

This diagram summarizes and visualizes some of the main aspects of the enhanced HTTP functionality in Configuration Manager.

![Conceptual diagram of enhanced HTTP functionality.](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/media/ehttp-diagram.svg)

- The connection with Microsoft Entra ID is recommended but optional. It enables scenarios that require Microsoft Entra authentication.
- When you enable the site option for enhanced HTTP, the site issues self-signed certificates to site systems such as the management point and distribution point roles.
- With the site systems still configured for HTTP connections, clients communicate with them over HTTPS.

## Frequently asked questions

### What are the benefits of enhanced HTTP?

The main benefit is to reduce the usage of pure HTTP, which is an insecure protocol. Configuration Manager tries to be secure by default, and Microsoft wants to make it easy for you to keep your devices secure. Enabling PKI-based HTTPS is a more secure configuration, but that can be complex for many customers. If you can't do HTTPS, then enable enhanced HTTP. Microsoft recommends this configuration, even if your environment doesn't currently use any of the features that support it.

Important

Starting in Configuration Manager version 2103, sites that allow HTTP client communication are deprecated. Configure the site for HTTPS or Enhanced HTTP. For more information, see [Enable the site for HTTPS-only or enhanced HTTP](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/list-of-prerequisite-checks#enable-site-system-roles-for-https-or-enhanced-http).

### Do I need to use Microsoft Entra ID to enable enhanced HTTP?

No. Many of the scenarios and features that benefit from enhanced HTTP rely on Microsoft Entra authentication. You can enable enhanced HTTP without onboarding the site to Microsoft Entra ID. It then supports features like the administration service and the reduced need for the network access account. You only need Microsoft Entra ID when one of the supporting features requires it.

Note

Even if you don't directly use the administration service REST API, some Configuration Manager features natively use it, including parts of the Configuration Manager console.

### How do clients communicate with site systems?

When you enable enhanced HTTP, the site issues certificates to site systems. For example, the management point and the distribution point. Then these site systems can support secure communication in currently supported scenarios.

From a client perspective, the management point issues each client a token. The client uses this token to secure communication with the site systems. That behavior is OS version agnostic, other than what the [Configuration Manager client supports](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).

### If some site systems are already HTTPS, can I enable enhanced HTTP?

Yes. Site systems always prefer a PKI certificate. For example, one management point already has a PKI certificate, but others don't. When you enable enhanced HTTP for the site, the HTTPS management point continues to use the PKI certificate. The other management points use the site-issued certificate for enhanced HTTP.

## Next steps

- [Plan for security](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/plan-for-security)
- [Security and privacy for Configuration Manager clients](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/security-and-privacy-for-clients)
- [Configure security](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/configure-security)
- [Communication between endpoints](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/communications-between-endpoints)
