<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac -->
<!-- Sitemap-Last-Modified: 2026-09-19 -->

# Microsoft Defender for Endpoint on macOS

Microsoft Defender for Endpoint on macOS helps your organization prevent, detect, investigate, and respond to threats on Mac devices. It uses Apple's system extension architecture and integrates with the Microsoft Defender portal for centralized security operations. Review the capabilities, requirements, and deployment methods before you install and onboard devices.

Defender for Endpoint on macOS includes the following core security capabilities:

- **Next-generation protection**: Provides real-time prevention against malware and emerging threats by using cloud-based machine learning, behavior monitoring, and heuristics.

  - **Real-time protection**: Uses [next-generation antivirus protection](https://learn.microsoft.com/en-us/defender-endpoint/next-generation-protection), local and cloud-based machine learning, behavior monitoring, and heuristics.
  - **Cloud-delivered protection**: Detects and blocks new and emerging threats, including infostealers and supply chain attacks.
  - **[Security settings configuration](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)**: Configure antivirus, cloud protection, and scan options, [detect and block potentially unwanted applications](https://learn.microsoft.com/en-us/defender-endpoint/mac-pua), and define custom [indicators of compromise](https://learn.microsoft.com/en-us/defender-endpoint/indicator-ip-domain) for IP addresses and URLs.
  - **[Network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection-macos) and [web protection](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-overview)**: Help protect Mac devices from web-based threats by controlling connections to malicious or unwanted sites.
  - **[Tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview)**: Protects security settings from unauthorized changes.
  - **[Device control](https://learn.microsoft.com/en-us/defender-endpoint/mac-device-control-overview)**: Monitors and restricts access to removable media, including USB storage, Bluetooth, and other peripherals. Deploy granular policies through [Intune](https://learn.microsoft.com/en-us/defender-endpoint/mac-device-control-configure#deploy-the-policy-by-using-microsoft-intune) or [Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-device-control-configure#deploy-the-policy-by-using-jamf-pro).

- **Endpoint detection and response \(EDR\)**: Provides visibility into endpoint activity for investigating and responding to advanced attacks.

  - **AI-driven detection**: Uses AI and advanced analytics to [detect and respond to threats](https://learn.microsoft.com/en-us/defender-endpoint/overview-endpoint-detection-response) in close to real time.
  - **Centralized management**: Use the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com) to view detections and manage devices.
  - **[Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)**: Query raw event data to proactively hunt for threats on Mac devices.
  - **[Response actions](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts)**: Run antivirus scans, isolate devices, collect investigation packages, and collect files for analysis.
  - **[Live response](https://learn.microsoft.com/en-us/defender-endpoint/live-response)**: Use a remote shell connection for investigation and response on macOS devices.

- **Posture management**: Provides risk-based vulnerability management, remediation, and tracking.

  - **[Vulnerability management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)**: Prioritize, remediate, and track vulnerabilities on Mac devices.
  - **[Exposure score](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-exposure-score)**: View your organization's risk exposure for managed Mac devices.
  - **[Security recommendations](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-recommendation)**: Review recommended actions to reduce endpoint risk.
  - **[Remediation tracking](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-remediation)**: Track remediation activities and exposure reduction.
  - **[Software inventory](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-software-inventory)**: View software installed on managed Mac devices.

- **Streamlined management and operations**: Supports deployment, configuration, and management through MDM tools and the Microsoft Defender portal.

  - **MDM integration**: Use [Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune), [Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-jamf), or [another MDM solution](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm) to deploy and manage Defender for Endpoint.
  - **[Security settings configuration](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)**: Configure security settings centrally. [Security settings management](https://learn.microsoft.com/en-us/intune/intune-service/protect/mde-security-integration) also lets you manage supported security policies from the Microsoft Defender portal without full Intune enrollment.
  - **[Software updates](https://learn.microsoft.com/en-us/defender-endpoint/mac-updates)**: Use Microsoft AutoUpdate \(MAU\) to keep Defender for Endpoint current.
  - **[Management APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/management-apis)**: Use APIs to integrate device management, vulnerability management, and threat intelligence with other systems.

- **Integration and extensibility**: Connects Defender for Endpoint with APIs, security information and event management \(SIEM\) solutions, and other Microsoft Defender products.

  - **[System extensions](https://learn.microsoft.com/en-us/defender-endpoint/mac-support-sys-ext)**: Use Apple's system extension architecture on supported Intel and Apple silicon processors.
  - **[API integration](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)**: Integrate Defender for Endpoint data and actions with other systems.
  - **SIEM connectors**: Connect security data to SIEM solutions for centralized monitoring and automated response.
  - **[Power BI support](https://learn.microsoft.com/en-us/defender-endpoint/api/api-power-bi)**: Create Power BI reports that use Defender for Endpoint data and role-based access control \(RBAC\).

## What's new in the latest release

For general updates, see [What's new in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/whats-new-in-microsoft-defender-endpoint). For macOS product builds and changes, see [What's new in Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-releases#macos-releases).

To send product feedback, open Microsoft Defender on the Mac device, and then select **Help** > **Send feedback**. To evaluate preview capabilities, configure the device to use the Beta update channel, formerly named `InsiderFast`.

## Deploy Defender for Endpoint on macOS

Choose a deployment method based on how your organization manages Mac devices. Each method installs the Microsoft Defender app, provides the required macOS permissions and configuration, onboards the device, and verifies connectivity to the Defender for Endpoint service.

Before you begin, review the [Defender for Endpoint on macOS prerequisites](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites), including licensing, supported operating systems, permissions, and network connectivity.

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

| Deployment method | Use this method when | Considerations |
| --- | --- | --- |
| [Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune) | Your organization manages Mac devices with Intune. | Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. You need a subscription that includes Intune, or you can buy it separately. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses). |
| [Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-jamf) | Your organization manages Apple devices with Jamf Pro. | Jamf Pro is a separate third-party product that requires its own subscription. The Jamf deployment uses separate articles for groups, profiles and policies, packages, and device enrollment. |
| [Another mobile device management solution](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm) | Your organization uses an MDM solution other than Intune or Jamf Pro. | The MDM solution must support package deployment and device-level Apple configuration profiles. Microsoft support doesn't cover third-party product behavior. |
| [Manual deployment](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-manually) | You need to install Defender for Endpoint on an individual evaluation or test device without using MDM. | A local administrator must install the app and approve the required macOS permissions on the device. Use an MDM solution for centrally managed production deployments. |

The exact steps depend on the selected deployment method, but every deployment has the following stages:

1. Prepare the network and confirm that the device meets the [system requirements](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites#system-requirements).
2. Approve or preapprove the required system extensions and macOS permissions.
3. Install the Microsoft Defender application package.
4. Apply the onboarding package to associate the device with your organization.
5. Verify onboarding, connectivity, antivirus protection, and endpoint detection and response \(EDR\).

### Verify the deployment

After installation and onboarding, confirm that the device reports an organization identifier and can connect to the Defender for Endpoint service:

- Check the organization identifier:

  ```bash
  mdatp health --field org_id
  ```

- Test service connectivity:

  ```bash
  mdatp connectivity test
  ```

Run an [antivirus detection test](https://learn.microsoft.com/en-us/defender-endpoint/validate-antimalware) and an [EDR detection test](https://learn.microsoft.com/en-us/defender-endpoint/edr-detection) to confirm that the device reports detections and alerts to the Microsoft Defender portal.

## Related content

- [Review the prerequisites for Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites)
- [Resources for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-resources)
- [Configure Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
