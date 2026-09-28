<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/fasttrack/windows-365-and-app-assure -->
<!-- Sitemap-Last-Modified: 2026-05-05 -->

# Windows 365 and App Assure

## Windows 365

FastTrack provides remote guidance for onboarding to Windows 365 Enterprise, Windows 365 Flex, and Windows 365 Government. Windows 365 takes the operating system to the Microsoft Cloud, securely streaming the full Windows experience—including all your apps, data, and settings—to your personal or corporate devices. Organizations can provision Windows 365 Cloud PCs \(devices that are deployed on the Windows 365 service\) instantly across the globe and manage them seamlessly alongside your physical PC estate using Microsoft Intune admin center. This desktop-as-a-service \(DaaS\) solution combines the benefits of desktop cloud hosting with the simplicity, security, and insights of Microsoft 365.

Remote guidance includes:

- Assigning licenses to users.
- Explaining the different feature set of Windows 365, Use Cases and Personas.
- Deploying Cloud PCs using the Microsoft Hosted Network \(MHN\) deployment mode. Represents Microsoft’s recommended scenario offering \(SaaS\) features of simplicity, reliability, and scalability.
- Creating and modifying Azure network connections \(ANCs\).
- Adding and deleting device images, including standard Azure Marketplace gallery images and custom images. Some guidance might be provided around deploying language packs with custom images using the Windows 365 language installer script.
- Creating, editing, and deleting provisioning policies, including settings policies and Autopilot device-preparation policies.
- Assisting with dynamic query expressions for dynamic groups and filtering.
- Enabling Windows passwordless authentication using Windows Hello for Business cloud trust for the use of Windows 365.
- Deploying Windows Update policies for Windows 365 Cloud PCs using Intune and Autopatch.
- Deploying apps \(including Microsoft 365 Apps for enterprise and Microsoft Teams with media optimizations\) to Windows 365 Cloud PCs using Microsoft Intune.
- Deploying Windows 365 Cloud Apps provisioning policies – Customer is responsible of creating the custom image, app installation and Intune Application Packaging.
- Deploying Windows 365 Reserve provisioning policies.
- Deploying Windows 365 User Experience Sync.
- Deploying Disaster Recovery Plus and Cross Region Disaster Recovery features.
- Provision a Cloud PC for an external identity - external identity support allows you to invite users to your Entra ID tenant and provide them with Cloud PCs.
- Securing Windows 365 Cloud PCs, including Conditional Access, multifactor authentication \(MFA\), and managing Remote Desktop Protocol \(RDP\) device redirections.
- Managing Windows 365 Cloud PCs on Microsoft Intune admin center, including remote actions, resizing, and other administrative tasks.
- Optimizing end user experience.
- Deploying and managing Windows 365 Flex Cloud PCs.
- Deploying and managing Windows 365 Government Cloud PCs.
- Deploying Windows 365 Boot.
- Deploying Windows 365 Client Access \(Windows App, Browser Access\).
- Supporting Windows 365 Link, including:

  - Providing an overview of Windows 365 Link, its capabilities, and use cases.
  - Preparing for deployment and requirements, including enabling single sign-on \(SSO\).
  - Deploying Windows 365 Link.
  - Managing, updating, and securing Windows 365 Link with Microsoft Intune.
  - Providing guidance on troubleshooting Windows 365 Link.

Note

See [Microsoft Defender XDR](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/microsoft-defender#microsoft-defender-xdr) and [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/microsoft-defender#microsoft-defender-for-endpoint) for details about Microsoft Defender for Endpoint and the security baseline scope as it applies to Windows 365.

### Out of scope

- Creation of Azure subscription features including Azure Virtual Networks \(VNets\), ExpressRoute, and Site-to-Site \(S2S\) VPN.
- Support for advanced networking topics.
- Customizing images for a Windows 365 Cloud PC on behalf of customers.
- Standalone use of Configuration Manager for managing Windows 365 Cloud PCs.
- Deploying Windows updates for Windows 365 Cloud PCs using Configuration Manager.
- Migrating virtual desktop infrastructure \(VDI\) or Azure Virtual Desktop virtual machines to Windows 365.
- Migrating Configuration Manager or Microsoft Deployment Toolkit \(MDT\) images to Azure.
- Migrating user profiles to or from Windows PCs.
- Configuring network appliances on behalf of customers.
- Programmatic actions using Microsoft Graph API.
- Support for non-Microsoft integrations.
- Support for Windows 365 Business.
- Windows 365 Link:

  - Providing hardware support.
  - Providing support for non-Microsoft product and feature integrations.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with items out of scope and/or if source environment expectations aren't met. If facing concerns about app compatibility, contact [Microsoft App Assure](https://go.microsoft.com/fwlink/?linkid=2247521).

### Source environment expectations

Before onboarding the following is required:

- Windows 365 [licensing requirements](https://learn.microsoft.com/en-us/windows-365/enterprise/requirements) must be met.
- If not using a Microsoft-hosted network:

  - An Azure subscription associated with the Microsoft Entra tenant where licenses are deployed must be used.
  - A virtual network is deployed in a region that's supported for Windows 365. The virtual network should:

    - Have sufficient private IP addresses for the number of Windows 365 Cloud PCs in order to deploy.
    - Have connectivity to Active Directory \(only for Microsoft Entra hybrid joined configuration\).
    - Have DNS servers configured for internal name resolution.

Note

FastTrack doesn't provide onboarding assistance for Azure Virtual Desktop. Customers should work with an Azure partner for Azure Virtual Desktop assistance.

## App Assure

App Assure is a service designed to address issues with Windows and Microsoft 365 Apps app compatibility and is available to all Microsoft customers. When you request the App Assure service, we will work with you to address valid app issues. To request App Assure assistance, complete the [App Assure service request](https://aka.ms/AppAssureRequest).

App Assure also provides assistance for apps deployed on the following Microsoft products:

- Windows 10/11 \(including Arm64 devices\).
- Microsoft 365 Apps, including Microsoft Copilot. App Assure supports Microsoft Copilot customers by addressing app compatibility issues encountered when moving to a monthly update channel.
- Microsoft Edge - For deployment guidance, see [Overview of the](https://learn.microsoft.com/en-us/DeployEdge/microsoft-edge-channels) [Microsoft Edge channels](https://learn.microsoft.com/en-us/DeployEdge/microsoft-edge-channels).
- Azure Virtual Desktop - For more information, see [What is Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/overview)? and [Windows 10 Enterprise multi-session FAQ](https://learn.microsoft.com/en-us/azure/virtual-desktop/windows-10-multisession-faq).
- Windows 365 Cloud PC - For more information, see [Introducing a new era of hybrid personal computing: the Windows 365 Cloud PC](https://go.microsoft.com/fwlink/?linkid=2247522).
- Microsoft Sentinel Codeless Connector Framework App Assure helps ensure customers can take full advantage of solutions built on the Microsoft Sentinel Codeless Connector Framework \(CCF\). We are committed to making every reasonable effort to resolve any issues that may hinder your ability to benefit from CCF. See [App Assure’s promise: Migrate to Sentinel with confidence](https://techcommunity.microsoft.com/blog/microsoftsentinelblog/app-assure%E2%80%99s-promise-migrate-to-sentinel-with-confidence/4404136).

### Out of scope

- App inventory and testing to determine what does and doesn’t work on Windows and Microsoft 365 Apps. For more information, see the [Windows and Office 365 deployment lab kit](https://learn.microsoft.com/en-us/microsoft-365/enterprise/modern-desktop-deployment-and-management-lab).
- Researching non-Microsoft ISV apps for Windows compatibility and support statements.
- App packaging-only services. However, the App Assure team packages Windows apps that we remediated to ensure they can be deployed in the customer's environment.
- Although Android apps on Windows 11 are available to Windows Insiders, App Assure doesn’t currently support Android apps or devices, including Surface Duo devices.

### Customer responsibilities

- Creating an app inventory.
- Validating those apps on Windows and Microsoft 365 Apps.

Note

Microsoft can’t make changes to your source code. However, the App Assure team can provide guidance to app developers if the source code is available for your apps.

Contact a [Microsoft Partner](https://go.microsoft.com/fwlink/?linkid=2080150) for assistance with these services.

### Source environment expectations

#### Windows and Microsoft 365 Apps

- Apps that worked on Windows 7, Windows 8.1, Windows 10, and Windows 11 also work on Windows 10/11.
- Apps that worked on Office 2010, Office 2013, Office 2016, and Office 2019 also work on Microsoft 365 Apps \(32-bit and 64-bit versions\).

#### Windows 365 Cloud PC

Apps that worked on Windows 7, Windows 8.1, Windows 10, and Windows 11 also work on Windows 365 Cloud PC.

#### Windows on Arm

Apps that worked on Windows 7, Windows 8.1, Windows 10, and Windows 11 also work on Windows 10/11 on Arm64 devices.

Note

x64 \(64-bit\) emulation is available on Windows 11 on Arm devices.

#### Microsoft Edge

If your web apps or sites work on supported versions of Google Chrome or any version of Microsoft Edge, they’ll also work on the latest version of Microsoft Edge. As the web is constantly evolving, be sure to review this published list of [known site compatibility-impacting changes for Microsoft Edge.](https://learn.microsoft.com/en-us/microsoft-edge/web-platform/site-impacting-changes)

Note

App Assure helps you configure IE mode to support legacy Internet Explorer web apps or sites. Support for development to modernize Internet Explorer web apps or sites to run natively on the Chromium engine isn’t covered under this benefit.

#### Azure Virtual Desktop

Apps running on Windows 7, Windows 8.1, Windows 10, Windows 11, or Windows Server \(as virtualized apps\) also run on:

- Windows 10/11 Enterprise.
- Windows 10/11 Enterprise multi-session.

Note

Windows Enterprise multi-session compatibility exclusions and limitations include:

- Limited redirection of hardware.
- A/V-intensive apps might perform in a diminished capacity.
- 16-bit apps aren’t supported for 64-bit Azure Virtual Desktop.

### Arm Advisory Service

The App Assure Arm Advisory Service is a no-cost service available to Windows on Arm developers where App Assure engineers assist with porting applications to Arm and building Arm-native applications.

Remote guidance for:

- Delivering a technical workshop for developing best practices, including answering specific implementation questions.
- Suggesting which platform features can be used to enhance application experience.
- Providing code review and code samples to enable development.
- Providing break-fix assistance if issues arise while building or porting apps.
- Providing engineering escalation to enable software development efforts and provide product feedback.

To contact App Assure for this service, complete the [Windows Arm Advisory Service](https://aka.ms/AppAssureRequest) enrollment form.

Note

Developers without access to Arm-based hardware can [create a Windows on Arm virtual machine](https://learn.microsoft.com/en-us/windows/arm/create-arm-vm) to develop, build, and test applications in a native environment.

Important

Be aware that Microsoft reserves the right to limit this offer to 15 hours per Arm developer and to waitlist developers due to high volume.
