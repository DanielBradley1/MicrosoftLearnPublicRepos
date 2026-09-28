<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/fasttrack/microsoft-intune -->
<!-- Sitemap-Last-Modified: 2026-05-04 -->

# Microsoft Intune

## Zero Trust

FastTrack provides comprehensive guidance on implementing Zero Trust security principles. The Zero Trust model assumes breach and verifies each request as though it originates from an uncontrolled network. This approach ensures robust security across your networks, applications, and environment. FastTrack accomplishes this by focusing on identity, devices, applications, data, infrastructure, and networks. With FastTrack, you can confidently advance your Zero Trust security journey and protect your digital assets effectively.

With Microsoft Intune, you can implement Zero Trust principles by securely provisioning, configuring, and updating all endpoint devices. This includes enforcing security policies through the cloud, covering endpoint security, device configuration, app protection, and compliance. This approach helps prevent data leaks to untrusted apps or services and ensures prompt responses to security compromises.

## Microsoft Intune

Microsoft Intune is a cloud-based endpoint management solution. It manages user access to organizational resources and simplifies app and device management across your devices, including mobile devices, desktop computers, and virtual endpoints. You can protect access and data on organization-owned and users' personal devices.

Intune has compliance and reporting features that support the Zero Trust security model.

FastTrack provides remote guidance for:

- Licensing your end users.
- Configuring identities used by Intune by using either on-premises Active Directory or cloud identities \(Microsoft Entra ID\).
- Adding users to your Intune subscription, defining IT admin roles, and creating user and device groups.
- Configuring your mobile device management \(MDM\) authority, based on management needs, including setting Intune as your MDM authority when Intune is the only MDM solution.
- Providing MDM guidance for:

  - Configuring tests groups to be used to validate MDM management policies.
  - Configuring MDM management policies and services including:

    - App deployment for each supported platform through web links or deep links.
    - Conditional Access policies.
    - Deployment of email, wireless networks, VPN profiles for existing certificate authority, wireless network, or VPN infrastructure in the organization.
    - Connecting to the Intune Data Warehouse.
    - Integrating Intune with:

      - TeamViewer for remote assistance \(a TeamViewer subscription is required\).
      - Mobile Threat Defense \(MTD\) partner solutions \(an MTD subscription is required\).
      - A telecom expense management solution \(a telecom expense management solution subscription is required\).

    - Enrolling devices of each supported platform to Intune.
    - Configuring endpoint security policies including Windows Local Administrator Password Solution \(LAPS\) using Intune.

- Providing app protection guidance on:

  - Configuring app protection policies for each supported platform.
  - Configuring Conditional Access policies for managed apps.
  - Targeting the appropriate user groups with the previously mentioned MAM policies.
  - Using managed-apps usage reports.

- Providing migration guidance from legacy PC management to Intune MDM.

### Out of scope

- Setting up or configuring certificate authorities, wireless networks, VPN infrastructures, or Apple MDM push certificates for Intune.
- Setting up or upgrading either the Configuration Manager site server or client to the minimum requirements needed to support cloud-attach.
- Integrating Intune with Microsoft Defender for Endpoint and creating device compliance policies based on its Windows 10 risk level assessment. FastTrack doesn't assist with purchasing, licensing, or activation.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with any out-of-scope services.

## Copilot in Intune

FastTrack provides remote guidance for:

- Onboarding assistance, including:

  - Provisioning Security Compute Units \(SCUs\).

Note

All M365 E5 customer tenants are automatically provisioned and onboarded to Security Copilot.

- Configuring default environments with necessary roles and permissions, and enabling Security Copilot embedded experiences.
- Walkthroughs for Copilot in Intune embedded experiences, including:

  - Using Copilot in Intune to troubleshoot device issues and assist with root cause assessment
  - Using Copilot in Intune for policy management to summarize existing settings, overall security impact, and providing guidance on best practices.
  - Using Copilot in Intune for running device queries and creating Kusto Query Language \(KQL\).

### Out of scope

- Detailed pricing information. Contact your account team for more information.
- Providing walkthroughs of standalone experiences.
- Creating new custom agents.
- Deploying third-party agents.

## Certificate delivery

FastTrack provides remote guidance for:

- Simple Certificate Enrollment Protocol \(SCEP\) and the Network Device Enrollment Service \(NDES\).

  - Configuring enterprise Certificate Authority-related items.
  - Creating and issuing a SCEP certificate template.
  - Installing and configuring NDES.
  - Installing and configuring the Microsoft Intune Connector for SCEP.
  - Installing and configuring Microsoft Entra application proxy and Microsoft Entra application connectors.
  - Creating and assigning a trusted certificate device configuration profile in Microsoft Intune admin center.
  - Creating and assigning a SCEP certificate device configuration profile on Microsoft Intune admin center.

- Public-Key Cryptography Standards \(PKCS\) and PFX \(PKCS#12\) certificates.

  - Configuring enterprise Certificate Authority-related items.
  - Creating and issuing a PKCS certificate template.
  - Installing and configuring a PFX certificate connector.
  - Creating and assigning a trusted certificate device configuration profile in Microsoft Intune admin center.
  - Creating and assigning a PKCS certificate device configuration profile in Microsoft Intune admin center.

### Out of scope

- Assistance with public key infrastructure \(PKI\) certificates or enterprise Certificate Authority.

  - Supporting advanced scenarios, including:

    - Placing the NDES server in the customer's DMZ.
    - Configuring or using a Web Application Proxy server to publish the NDES URL externally to the corporate network. We recommend and provide guidance for using the Microsoft Entra application proxy to accomplish configuration.
    - Using imported PKCS certificates.
    - Configuring Intune certificate deployment using a hardware security module \(HSM\).

## Cloud-attach

FastTrack provides remote guidance to customers to cloud-attach existing Configuration Manager environments with Intune.

This guidance includes:

- Licensing end users.
- Configuring identities to be used by Intune by using on-premises Active Directory and cloud identities.
- Adding users to your Intune subscription, defining IT admin roles, and creating user and device groups.
- Providing guidance setting up Microsoft Entra hybrid join.
- Providing guidance on setting up Microsoft Entra ID for MDM autoenrollment.
- Providing guidance on how to set up cloud management gateway when used as a solution for co-management of remote internet-based device management.
- Configuring supported workloads to switch to Intune.
- Installing the Configuration Manager client on Intune-enrolled devices.

## Deploy Outlook mobile for iOS and Android securely

FastTrack provides remote guidance to customers to deploy Outlook mobile for iOS and Android securely to ensure users have all required apps installed.

This guidance includes:

- Downloading Outlook for iOS and Android, Microsoft Authenticator, and Intune Company Portal apps through the Apple App Store or Google Play Store.
- Setting up:

  - The Outlook for iOS and Android, Microsoft Authenticator, and Intune Company Portal apps deployment with Intune.
  - App protection policies.
  - Conditional Access policies.
  - App configuration policies.

## Endpoint analytics

FastTrack provides remote guidance to customers to enable Endpoint analytics.

This guidance includes:

- Confirming the licenses for your endpoints and users.
- Confirming your organizational environments meet the prerequisites for Endpoint analytics features.
- Configuring endpoints with correct policies to enable Endpoint analytics features.
- Setting organizational baselines to track progress.
- Providing guidance on using Remediation within Endpoint analytics, including:

  - Using Microsoft-authored remediation scripts.

### Out of scope

- Creating custom remediation scripts.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with any out-of-scope services.

### Source environment expectations

- IT admins must have existing certificate authority, wireless network, and VPN infrastructures enabled in their production environments in order to deploy wireless network and VPN profiles with Intune.
- The customer environment should have an existing healthy PKI before enabling PKCS and SCEP certificate delivery with Intune.
- Intune must manage Endpoint devices.
- IT admins are responsible for registering the devices to the organization by either having the hardware vendor upload the hardware IDs for uploading it themselves into the Windows Autopilot service.

## Microsoft Intune Suite

Microsoft Intune Suite provides mission-critical advanced endpoint management and security capabilities for Intune.

### Endpoint Privilege Management

Endpoint Privilege Management \(EPM\) supports your zero-trust journey by helping your organization achieve a broad user base running with least privilege while allowing users to still run tasks allowed by your organization and remain productive.

FastTrack provides remote guidance to customers to enable EPM.

This guidance includes:

- Providing an overview of EPM, prerequisites, and endpoints.
- Providing guidance on enabling EPM and elevation setting policies and default responses for elevation requests.
- Providing guidance for creating elevation rules policies to manage the identification of specific files and how elevation requests for those files are handled.
- Creating reusable settings groups to manage the certificates already in place.
- Providing guidance for policy conflict handling.
- Providing support-approved file elevations.
- Providing role-based access control \(RBAC\) permissions for elevation requests.
- Creating policies for support-approved file elevations.
- Managing pending elevation requests.
- Providing EPM reports.

#### Out of scope

- Managing pending approvals using automation.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with any out-of-scope services.

For more information, see [Use Endpoint Privilege Management with Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/protect/epm-overview).

### Enterprise Application Management

Enterprise Application Management provides an Enterprise App Catalog of Win32 apps that are easily accessible in Intune. You can add these apps to your tenant by selecting them from the Enterprise App Catalog. When you add an Enterprise App Catalog app to your Intune tenant, default installation, requirements, and detection settings are automatically provided. In addition, Intune hosts Enterprise App Catalog apps in Microsoft storage.

FastTrack provides remote guidance to customers to enable Enterprise Application Management.

This guidance includes:

- Providing an overview of and prerequisites for Enterprise Application Management.
- Configuring prepackaged and pre-configured apps that are self-updating.
- Adding the Windows Catalog app to Intune.
- Enabling app information monitoring.
- Enabling app installation status reports.

#### Out of scope

- Automation using Microsoft Graph API.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with any out-of-scope services.

For more information, see [Microsoft Intune Enterprise Application Management](https://learn.microsoft.com/en-us/mem/intune/apps/apps-enterprise-app-management).

### Advanced Analytics

Advanced Analytics is a set of analytics-driven capabilities that help IT admins understand, anticipate, and improve the end-user experience.

FastTrack provides remote guidance to customers to enable Advanced Analytics.

This includes:

- Providing an overview of and prerequisites for Advanced Analytics.
- Enabling anomaly detection in Endpoint analytics to monitor the health of devices for user experience and productivity regressions following configuration changes.
- Providing an enhanced device timeline of events on a specific device to assist with troubleshooting device issues.
- Configuring device scopes in Endpoint analytics, including custom device scopes to slice Endpoint analytics reports to a subset of devices.
- Configuring device queries in Intune, including near-real time access to data about device state.
- Enabling battery health reports.

#### Source environment expectations

- The customer uses Intune for device management.

For more information, see [What is Microsoft Intune Advanced Analytics?](https://learn.microsoft.com/en-us/intune/advanced-analytics/).

### Remote Help

Remote Help is a cloud-based solution for secure help desk connections with role-based access controls \(RBAC\).

FastTrack provides remote guidance to customers to enable Remote Help.

This includes:

- Providing an overview of and prerequisites for Remote Help.
- Clarifying the prerequisites for Remote Help on Windows, Android, and macOS.
- Configuring Remote Help for the customer's tenant.
- Configuring RBAC to set the level of access a helper is allowed.
- Configuring Remote Help on Windows enrolled and unenrolled devices, including:

  - Clarifying network considerations.
  - Installing and updating the Remote Help Win32 App.
  - Enabling log files

- Configuring Remote Help to work with Conditional Access.
- Configuring the ServiceNow connector.
- Configuring Remote Help on macOS enrolled and unenrolled devices, including:

  - Clarifying network considerations.
  - Installing the Remote Help app,
  - Configuring native app OS permissions.
  - Installing and updating the Remote Help native macOS app.

- Configuring Remote Help on Android devices, including:

  - Clarifying the prerequisites.
  - Deploying the Remote Help app.
  - Providing guidance on granting permissions for Zebra and Samsung devices.
  - Using Remote Help on Android devices.

#### Out of scope

- ServiceNow integration and troubleshooting.
- Configuring original equipment manufacturer \(OEM\) Android devices.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with any out-of-scope services.

For more information, see [Use Remote Help with Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/fundamentals/remote-help).

### Microsoft Tunnel for Mobile Application Management

When you use the Microsoft Tunnel VPN Gateway, you can extend Microsoft Tunnel support by adding Tunnel for Mobile Application Management \(MAM\). Tunnel for MAM extends the Microsoft Tunnel VPN Gateway to support devices that run Android or iOS and that aren't enrolled with Intune.

FastTrack provides remote guidance to customers to enable Tunnel for MAM.

This includes:

- Providing an overview of and prerequisites for Tunnel for MAM.
- Configuring Microsoft Tunnel VPN for unenrolled Android devices.
- Configuring policies to support Tunnel for MAM.
- Configuring line-of-business \(LOB\) apps.
- Configuring Microsoft Tunnel VPN for unenrolled iOS and iPad devices.
- Reviewing the required SDK for iOS.
- Configuring policies for Tunnel for MAM for iOS.
- Configuring LOB apps in Microsoft Entra admin center.
- Configuring Xcode LOB apps integration.
- Monitoring Microsoft Tunnel.

#### Out of scope

- Core Microsoft Tunnel Gateway setup.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with any out-of-scope services.

For more information, see [Microsoft Tunnel for Mobile Application Management](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-tunnel-mam).

### Microsoft Cloud PKI

Microsoft Cloud PKI is a cloud-based service that simplifies and automates certificate lifecycle management for Intune-managed devices. It provides a dedicated public key infrastructure \(PKI\) for your organization and handles the certificate issuance, renewal, and revocation for all Intune-supported platforms.

FastTrack provides remote guidance to customers to enable Microsoft Cloud PKI.

This includes:

- Providing an overview of and prerequisites for Microsoft Cloud PKI.
- Configuring RBAC-created custom roles with Microsoft Cloud PKI permissions.
- Creating a two-tier PKI hierarchy with both root and issuing certification authority \(CA\) in the cloud.
- Configuring bring your own CA \(BYOCA\) to anchor an Intune-issuing CA to a private CA through Active Directory Certificate Services or a non-Microsoft certificate service.
- Creating trusted certificate profiles.
- Creating Simple Certificate Enrollment Protocol \(SCEP\) certificate profiles.
- Monitoring the issuing CA and reviewing issued certificates.
- Providing a SCEP certificate profile report.
- Enabling Microsoft Cloud PKI audit logs.

#### Out of scope

- Explaining cryptographic concepts.
- Setting up or configuring on-premises CAs.
- Configuring CAs for web service enrollment.
- Deploying certificates on relying parties \(like VPN, Wi-Fi, apps, or servers\).
- Configuring your Network Policy Server \(NPS\) or Remote Authentication Dial-In User Service \(RADIUS\).

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with any out-of-scope services.

For more information, see [Overview of Microsoft Cloud PKI for Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-cloud-pki-overview).

### Firmware Over-the-Air updates and specialty device management

Firmware Over-the-Air \(FOTA\) updates allow for remote updating of device firmware using a wireless connection rather than requiring the devices to be physically connected to a computer or network.

Specialty device management with Intune provides a range of management, configuration, and protection capabilities for specialized devices, like AR and VR headsets, large smart-screen devices, and select conference room meeting devices.

FastTrack provides remote guidance to customers to enable FOTA updates and specialty device management.

This includes:

- Setting up Intune enrollment for Android devices on the Android Open Source Project \(AOSP\) platform for corporate-owned user-less and user-associated devices \(including RealWear devices\).
- Enabling Android FOTA updates.
- Enabling Samsung Enterprise FOTA \(E-FOTA\) update management.
- Enabling Zebra LifeGuard Over-the-Air \(LG OTA\) integration.
- Configuring Meta Work Accounts for automatic user provisioning with Microsoft Entra ID.
- Configuring automatic user provisioning for Meta Quest for Business Work Accounts with Microsoft Entra ID.
- Monitoring provisioning logs.
- Setting up the Meta Quest Device Manager.
- Configuring Intune integration with Meta Quest Device Manager.

#### Out of scope

- Meta Quest for Business troubleshooting.
- OEM configuration and integration troubleshooting.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with any out-of-scope services.

For more information, see [Mobile Firmware-over-the-air update](https://learn.microsoft.com/en-us/mem/intune/fundamentals/intune-add-ons#mobile-firmware-over-the-air-update).

### Microsoft advanced deployment guides

Microsoft provides customers with technology and guidance to assist with deploying your Microsoft 365, Microsoft Viva, and security services. We encourage our customers to start their deployment journey with [these](https://go.microsoft.com/fwlink/?linkid=2226341) offerings.

For non-IT admins, see [Microsoft 365 Setup](https://go.microsoft.com/fwlink/?linkid=2247616).

Note

If deployment guidance for a product isn't listed in the FastTrack service, complete the Request for Assistance form, to ensure you're directed to the most appropriate resources for your deployment goals and organizational needs. Once submitted, your request is reviewed and routed to a resource who can best support your deployment goals.

Note

*Note that the scope and SLA of support might vary depending on the specific workload. FastTrack can help recommend resources from self-guidance, Microsoft Unified offerings, or Microsoft partners to meet your deployment needs.*
