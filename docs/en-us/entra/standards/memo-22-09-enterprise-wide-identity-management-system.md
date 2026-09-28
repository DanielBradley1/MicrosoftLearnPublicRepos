<!-- Source: https://learn.microsoft.com/en-us/entra/standards/memo-22-09-enterprise-wide-identity-management-system -->
<!-- Sitemap-Last-Modified: 2025-02-10 -->

# Memo 22-09 enterprise-wide identity management system

[M-22-09 Memorandum for Heads of Executive Departments and Agencies](https://bidenwhitehouse.archives.gov/wp-content/uploads/2022/01/M-22-09.pdf) requires agencies to develop a consolidation plan for their identity platforms. The goal is to have as few agency-managed identity systems as possible within 60 days of the publication date \(March 28, 2022\). There are several advantages to consolidating identity platform:

- Centralize management of identity lifecycle, policy enforcement, and auditable controls
- Uniform capability and parity of enforcement
- Reduce the need to train resources across multiple systems
- Enable users to sign in once and then access applications and services in the IT environment
- Integrate with as many agency applications as possible
- Use shared authentication services and trust relationships to facilitate integration across agencies

## Why Microsoft Entra ID?

Use Microsoft Entra ID to implement recommendations from memorandum 22-09. Microsoft Entra ID has identity controls that support Zero Trust initiatives. With Microsoft Office 365 or Azure, Microsoft Entra ID is an identity provider \(IdP\). Connect your applications and resources to Microsoft Entra ID as your enterprise-wide identity system.

## Single sign-on requirements

The memo requires users sign in once and then access applications. With Microsoft single sign-on \(SSO\) users sign in once and then access cloud services and applications. See, [Microsoft Entra seamless single sign-on](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-sso).

## Integration across agencies

Use Microsoft Entra B2B collaboration to meet the requirement of facilitating integration and collaboration across agencies. Users can reside in a Microsoft tenant in the same cloud. Tenants can be on another Microsoft cloud, or in a non-Azure AD tenant \(SAML/WS-Fed identity provider\).

With Microsoft Entra cross-tenant access settings, agencies manage how they collaborate with other Microsoft Entra organizations and other Microsoft Azure clouds:

- Limit what Microsoft tenants users can access
- Settings for external user access, including multifactor authentication enforcement and device signal

Learn more:

- [B2B collaboration overview](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)
- [Microsoft Entra B2B in government and national clouds](https://learn.microsoft.com/en-us/entra/external-id/b2b-government-national-clouds)
- [Federation with SAML/WS-Fed identity providers for guest users](https://learn.microsoft.com/en-us/entra/external-id/direct-federation)

## Connecting applications

To consolidate and use Microsoft Entra ID as the enterprise-wide identity system, review the assets that are in scope.

### Document applications and services

Create an inventory of the applications and services users access. An identity management system protects what it knows.

Asset classification:

- The sensitivity of data therein
- Laws and regulations for confidentiality, integrity, or availability of data and/or information in major systems

  - Said laws and regulations that apply to system information protection requirements

For your application inventory, determine applications that use cloud-ready protocols or legacy authentication protocols:

- Cloud-ready applications support modern protocols for authentication:

  - SAML
  - WS-Federation/Trust
  - OpenID Connect \(OIDC\)
  - OAuth 2.0.

- Legacy authentication applications rely on older or proprietary authentication methods:

  - Kerberos/NTLM \(Windows authentication\)
  - Header-based authentication
  - LDAP
  - Basic authentication

Learn more [Microsoft Entra integrations with authentication protocols](https://learn.microsoft.com/en-us/entra/architecture/auth-sync-overview).

#### Application and service discovery tools

Microsoft offers the following tools to support application and service discovery.

| Tool | Usage |
| --- | --- |
| Usage Analytics for Active Directory Federation Services \(AD FS\) | Analyzes federated server authentication traffic. See, [Monitor AD FS using Microsoft Entra Connect Health](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-health-adfs) |
| Microsoft Defender for Cloud Apps | Scans firewall logs to detect cloud apps, infrastructure as a service \(IaaS\) services, and platform as a service \(PaaS\) services. Integrate Defender for Cloud Apps with Defender for Endpoint to discovery data analyzed from Windows client devices. See, [Microsoft Defender for Cloud Apps overview](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps) |
| Application Discovery worksheet | Document the current states of your applications. See, [Application Discovery worksheet](https://download.microsoft.com/download/2/8/3/283F995C-5169-43A0-B81D-B0ED539FB3DD/Application%20Discovery%20worksheet.xlsx) |

Your apps might be in systems other than Microsoft, and Microsoft tools might not discover those apps. Ensure a complete inventory. Providers need mechanisms to discover applications that use their services.

#### Prioritize applications for connection

After you discover the applications in your environment, prioritize them for migration. Consider:

- Business criticality
- User profiles
- Usage
- Lifespan

Learn more: [Migrate application authentication to Microsoft Entra ID](https://aka.ms/migrateapps/whitepaper).

Connect your cloud-ready apps in priority order. Determine the apps that use legacy authentication protocols.

For apps that use legacy authentication protocols:

- For apps with modern authentication, reconfigure them to use Microsoft Entra ID
- For apps without modern authentication, there are two choices:

  - Update the application code to use modern protocols by integrating the Microsoft Authentication Library \(MSAL\)
  - Use Microsoft Entra application proxy or secure hybrid partner access for secure access

- Decommission access to apps no longer needed, or that aren't supported

Learn more

- [Microsoft Entra integrations with authentication protocols](https://learn.microsoft.com/en-us/entra/architecture/auth-sync-overview)
- [What is the Microsoft identity platform?](https://learn.microsoft.com/en-us/entra/identity-platform/v2-overview)
- [Secure hybrid access: Protect legacy apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/secure-hybrid-access)

## Connecting devices

Part of centralizing an identity management system is enabling users to sign in to physical and virtual devices. You can connect Windows and Linux devices in your centralized Microsoft Entra system, which eliminates multiple, separate identity systems.

During your inventory and scoping, identify the devices and infrastructure to be integrated with Microsoft Entra ID. Integration centralizes your authentication and management by using Conditional Access policies with multifactor authentication enforced through Microsoft Entra ID.

### Tools to discover devices

You can use Azure Automation accounts to identify devices through inventory collection connected to Azure Monitor. Microsoft Defender for Endpoint has device inventory features. Discover the devices that have Defender for Endpoint configured and those that don't. Device inventory comes from on-premises systems such as System Center Configuration Manager or other systems that manage devices and clients.

Learn more:

- [Manage inventory collection from VMs](https://learn.microsoft.com/en-us/azure/automation/change-tracking/manage-inventory-vms)
- [Microsoft Defender for Endpoint overview](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/machines-view-overview)
- [Introduction to hardware inventory](https://learn.microsoft.com/en-us/mem/configmgr/core/clients/manage/inventory/introduction-to-hardware-inventory)

### Integrate devices with Microsoft Entra ID

Devices integrated with Microsoft Entra ID are hybrid-joined devices or Microsoft Entra joined devices. Separate device onboarding by client and user devices, and by physical and virtual machines that operate as infrastructure. For more information about deployment strategy for user devices, see the following guidance.

- [Plan your Microsoft Entra device deployment](https://learn.microsoft.com/en-us/entra/identity/devices/plan-device-deployment)
- [Microsoft Entra hybrid joined devices](https://learn.microsoft.com/en-us/entra/identity/devices/concept-hybrid-join)
- [Microsoft Entra joined devices](https://learn.microsoft.com/en-us/entra/identity/devices/concept-directory-join)
- [Log in to a Windows virtual machine in Azure by using Microsoft Entra ID including passwordless](https://learn.microsoft.com/en-us/entra/identity/devices/howto-vm-sign-in-azure-ad-windows)
- [Log in to a Linux virtual machine in Azure by using Microsoft Entra ID and OpenSSH](https://learn.microsoft.com/en-us/entra/identity/devices/howto-vm-sign-in-azure-ad-linux)
- [Microsoft Entra join for Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/architecture/example-scenario/wvd/azure-virtual-desktop-azure-active-directory-join)
- [Device identity and desktop virtualization](https://learn.microsoft.com/en-us/entra/identity/devices/howto-device-identity-virtual-desktop-infrastructure)

## Next steps

The following articles are part of this documentation set:

- [Meet identity requirements of memorandum 22-09 with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/standards/memo-22-09-meet-identity-requirements)
- [Meet multifactor authentication requirements of memorandum 22-09](https://learn.microsoft.com/en-us/entra/standards/memo-22-09-multi-factor-authentication)
- [Meet authorization requirements of memorandum 22-09](https://learn.microsoft.com/en-us/entra/standards/memo-22-09-authorization)
- [Other areas of Zero Trust addressed in memorandum 22-09](https://learn.microsoft.com/en-us/entra/standards/memo-22-09-other-areas-zero-trust)
- [Securing identity with Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/deploy/identity)
