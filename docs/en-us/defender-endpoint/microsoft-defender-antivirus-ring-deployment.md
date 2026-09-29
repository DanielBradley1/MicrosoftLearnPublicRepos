<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# Deploy Microsoft Defender Antivirus in rings

Microsoft Defender for Endpoint is an enterprise endpoint security platform designed to help enterprise networks prevent, detect, investigate, and respond to advanced threats.

Tip

Microsoft Defender for Endpoint is available in two plans, Defender for Endpoint Plan 1 and Plan 2. A new Microsoft Defender Vulnerability Management add-on is now available for Plan 2.

Deploying Microsoft Defender for Endpoint can be done using a ring-based deployment approach and updating using the gradual rollout process.

## Prerequisites

### Supported operating systems

- Windows
- Windows Server

## Ring deployment overview

It's important to ensure that client components are up to date to deliver critical protection capabilities and prevent attacks. Capabilities are provided through several components:

- [Endpoint Detection & Response](https://learn.microsoft.com/en-us/defender-endpoint/overview-endpoint-detection-response)
- [Next-generation protection](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows) with [cloud-delivered protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-microsoft-defender-antivirus)
- [Attack Surface Reduction](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-overview)

Updates are released monthly using a gradual release process. This process helps to enable early failure detection to identify problematic results in your unique environment as it occurs and address it quickly before a larger rollout.

Note

For more information on how to control daily security intelligence updates, see [Schedule Microsoft Defender Antivirus protection updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-protection-update-schedule-microsoft-defender-antivirus). Updates ensure that next-generation protection can defend against new threats, even if cloud-delivered protection is not available to the endpoint.

This article provides overview information about deploying Microsoft Defender Antivirus in rings for a gradual rollout process.

## Management tools

To create your own custom gradual rollout process for daily and/or monthly updates, you can use the following methods that use the tools:

- **Microsoft Intune and Microsoft Update** microsoft-intune-and-microsoft-update - Requires direct access to the internet. Microsoft Update \(MU\), formerly known as Windows Update \(WU\)
- **System Center Configuration Manager and Windows Server Update Services** - System Center Configuration Manager \(SCCM\) Software Update Point \(SUP\) = SCCM + Windows Server Update Services \(WSUS\)
- **Group Policy and Microsoft Update** - Requires direct access to the internet
- **Group Policy and network share** - For example, UNC path, SMB, CIFS
- **Group Policy and WSUS**

For details on how to use these tools, see [Create a custom gradual rollout process for Microsoft Defender updates](https://learn.microsoft.com/en-us/defender-endpoint/configure-updates).

Customers that prioritize availability over security, should take a crawl, walk, run approach.

## Deployment scenarios

- [Ring deployment using Intune and Microsoft Update](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-intune-microsoft-update)
- [Ring deployment using System Center Configuration Manager and Windows Server Update Services \(WSUS\)](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-sscm-wsus)
- [Ring deployment using Group Policy and Microsoft Update](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-group-policy-microsoft-update)
- [Ring deployment using Group Policy and network share](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-group-policy-network-share)
- Ring deployment using Group Policy and Windows Server Update Services

  - [Pilot ring deployment using Group Policy and Windows Server Update Services](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-pilot-ring-deployment-group-policy-wsus)
  - [Production ring deployment using Group Policy and Windows Server Update Services](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-production-ring-deployment-group-policy-wsus)
