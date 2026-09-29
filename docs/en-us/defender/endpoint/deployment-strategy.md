<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/deployment-strategy -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# Identify your architecture and select a deployment method for Defender for Endpoint

If you're already completed the steps to [prepare your environment for Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/production-deployment), and you have [assigned roles and permissions for Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/prepare-deployment), your next step is to create a plan for onboarding. This plan should begin with identifying your architecture and choosing your deployment method.

We understand that every enterprise environment is unique, so we've provided several options to give you the flexibility in choosing how to deploy the service. Deciding how to onboard endpoints to the Defender for Endpoint service comes down to two important steps:

![The deployment flow](https://learn.microsoft.com/en-us/defender/media/defender-endpoint/onboarding-architecture-2.png)

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

## Step 1: Identify your architecture

Depending on your environment, some tools are better suited for certain architectures. Use the following table to decide which Defender for Endpoint architecture best suits your organization.

| Architecture | Description |
| --- | --- |
| **Cloud-native** | We recommend using Microsoft Intune to onboard, configure, and remediate endpoints from the cloud for enterprises who don't have an on-premises configuration management solution or are looking to reduce their on-premises infrastructure. |
| **Co-management** | For organizations who host both on-premises and cloud-based workloads we recommend using Microsoft's ConfigMgr and Intune for their management needs. These tools provide a comprehensive suite of cloud-powered management features, and unique co-management options to provision, deploy, manage, and secure endpoints and applications across an organization. |
| **On-premises** | For enterprises who want to take advantage of the cloud-based capabilities of Microsoft Defender for Endpoint while also maximizing their investments in Configuration Manager or Active Directory Domain Services, we recommend this architecture. |
| **Evaluation and local onboarding** | We recommend this architecture for SOCs \(Security Operations Centers\) who are looking to evaluate or run a Microsoft Defender for Endpoint pilot, but don't have existing management or deployment tools. This architecture can also be used to onboard devices in small environments without management infrastructure, such as a DMZ \(Demilitarized Zone\). |

## Step 2: Select your deployment method

Once you have determined the architecture of your environment and have created an inventory as outlined in the [requirements section](https://learn.microsoft.com/en-us/defender-endpoint/mde-planning-guide#requirements), use the table below to select the appropriate deployment tools for the endpoints in your environment. This information will help you plan the deployment effectively.

| Endpoint | Deployment tool |
| --- | --- |
| **Windows client devices** | [Defender deployment tool](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows)  <br>[Microsoft Intune / Mobile Device Management \(MDM\)](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-mdm)  <br>[Microsoft Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-sccm)  <br>[Local script \(up to 10 devices\)](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script)  <br>[Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp)  <br>[Non-persistent virtual desktop infrastructure \(VDI\) devices](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-vdi)  <br>[Azure Virtual Desktop](https://learn.microsoft.com/en-us/defender-endpoint/onboard-windows-multi-session-device)  <br>[Defender deployment tool](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows), [System Center Endpoint Protection](https://learn.microsoft.com/en-us/defender-endpoint/onboard-downlevel), and [Microsoft Monitoring Agent](https://learn.microsoft.com/en-us/defender-endpoint/onboard-downlevel) \(Windows 8.1\) |
| **Windows Server**  <br>\(Requires a server plan\) | [Local script](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script)  <br>[Integration with Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/defender-endpoint/azure-server-integration)  <br>[Guidance for Windows Server with SAP](https://learn.microsoft.com/en-us/defender-endpoint/mde-sap-windows-server)  <br>[Defender deployment tool](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows) for Windows Server 2008 R2 SP1 |
| **macOS** | [Choose a macOS deployment method](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac#deploy-defender-for-endpoint-on-macos) |
| **Linux server**  <br>\(Requires a server plan\) | [Defender deployment tool](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-defender-deployment-tool)  <br>[Installer script based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-installer-script)  <br>[Ansible](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-ansible)  <br>[Chef](https://learn.microsoft.com/en-us/defender-endpoint/linux-deploy-defender-for-endpoint-with-chef)  <br>[Puppet](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-puppet)  <br>[Saltstack](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-saltack)  <br>[Manual deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-manually)  <br>[Direct onboarding with Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/onboard-machines-with-defender-for-endpoint)  <br>[Guidance for Linux with SAP](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-deployment-on-sap) |
| **Android** | [Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-deploy-android) |
| **iOS** | [Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/ios-install)  <br>[Mobile Application Manager](https://learn.microsoft.com/en-us/defender-endpoint/ios-install-unmanaged) |

Note

For devices that aren't managed by Intune or Configuration Manager, you can use the Defender for Endpoint Security Settings Management to receive security configurations directly from Intune. To onboard servers to Defender for Endpoint, [server licenses](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint) are required. You can choose from these options:

- [Microsoft Defender for Servers Plan 1 or Plan 2](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-servers-overview) \(as part of the Defender for Cloud\) offering
- Microsoft Defender for Endpoint for servers
- [Microsoft Defender for Business servers](https://learn.microsoft.com/en-us/defender-business/get-defender-business#how-to-get-microsoft-defender-for-business-servers) \(for small and medium-sized businesses only\)

## Next step

After choosing your Defender for Endpoint architecture and deployment method continue to [Step 4 - Onboard devices](https://learn.microsoft.com/en-us/defender-endpoint/onboarding).
