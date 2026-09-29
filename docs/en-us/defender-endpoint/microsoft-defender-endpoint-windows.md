<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-windows -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Microsoft Defender for Endpoint on Windows

Microsoft Defender for Endpoint on Windows provides preventative protection, post-breach detection, automated investigation, and response for Windows endpoints.

## Security capabilities for Windows environments

The following table describes the core security capabilities offered by Microsoft Defender for Endpoint on Windows.

| Capability | Description |
| --- | --- |
| **Autonomous protection** | Uses AI-driven automation to disrupt active attacks and proactively shield high-value assets. |
| **Next-generation protection** | Provides behavior-based, cloud-delivered, and machine-learning-powered antivirus protection with attack surface reduction. |
| **Endpoint detection and response \(EDR\)** | Delivers deep visibility into endpoint activity and enables rapid investigation and response to advanced attacks. |
| **Vulnerability management** | Identifies security gaps and prioritizes remediation actions to continuously reduce risk exposure. |
| **Automated investigation and response** | Uses automated playbooks to investigate alerts and apply remediation actions without manual intervention. |
| **Streamlined management and operations** | Simplifies deployment, configuration, and management through existing tools and the Defender portal. |
| **Seamless integration and extensibility** | Connects with SIEM solutions, Power BI, and the broader Defender suite for unified visibility. |
| **Device and network discovery** | Finds unmanaged endpoints and network devices to close visibility gaps. |

### Autonomous protection

The following capabilities use AI to detect and stop attacks without waiting for analyst action.

| Capability | Description |
| --- | --- |
| **[Automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption)** | Identifies and contains active attacks in real time by automatically isolating compromised devices and disabling compromised user accounts, stopping lateral movement before human intervention is needed. |
| **[Predictive shielding](https://learn.microsoft.com/en-us/defender-xdr/shield-predict-threats)** | Uses AI to anticipate threats and proactively shield high-value assets before an attack reaches them. |

### Next-generation protection

Protect Windows endpoints from malware and advanced threats using real-time, behavior-based, and cloud-powered protection capabilities.

| Capability | Description |
| --- | --- |
| **[Next-generation antivirus](https://learn.microsoft.com/en-us/defender-endpoint/next-generation-protection)** | Uses behavior-based, cloud-delivered, and machine-learning techniques to detect and block threats. |
| **[Behavioral blocking and containment](https://learn.microsoft.com/en-us/defender-endpoint/behavioral-blocking-containment)** | Detects and blocks malicious behaviors and helps contain compromised devices. |
| **[Web protection](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-overview)** | Guards against malicious websites, phishing attempts, and web-based threats. |
| **[Network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection)** | Blocks connections to malicious network destinations. |
| **[Attack surface reduction](https://learn.microsoft.com/en-us/defender-endpoint/overview-attack-surface-reduction)** | Reduces exposure to common attack techniques such as credential theft, malware execution, and unauthorized use of removable storage, including [ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction) and [device control](https://learn.microsoft.com/en-us/defender-endpoint/device-control-overview). |
| **[Tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview)** | Safeguards critical security settings from unauthorized changes. |
| **[Firewall](https://learn.microsoft.com/en-us/defender-endpoint/configure-environment)** | Configuration enables Defender for Endpoint service connectivity. |

### Endpoint detection and response \(EDR\)

Detect, investigate, and respond to sophisticated attacks powered by AI-driven analytics, behavioral detections, and Microsoft Threat Intelligence.

| Capability | Description |
| --- | --- |
| **AI-driven detection** | Uses AI and advanced analytics to [detect and respond to threats](https://learn.microsoft.com/en-us/defender-endpoint/overview-endpoint-detection-response) close to real time. |
| **Centralized management** | The Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com) provides a central location to view detections and manage your organization's devices. |
| **[Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)** | Enables proactive threat hunting by querying raw event data for deeper insight into network events. |
| **[Threat analytics](https://learn.microsoft.com/en-us/defender-endpoint/threat-analytics)** | Provides curated intelligence reports about active and emerging threats. |
| **[EDR in block mode](https://learn.microsoft.com/en-us/defender-endpoint/edr-in-block-mode)** | Enables Defender for Endpoint to block and remediate threats even when Microsoft Defender Antivirus runs in passive mode. |
| **[Response actions](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts)** | Includes running antivirus scans, isolating devices, collecting investigation packages, and collecting files for deep analysis. |
| **[Live response](https://learn.microsoft.com/en-us/defender-endpoint/live-response)** | Provides remote shell connections to perform in-depth investigations. |
| **[Endpoint Attack Notifications](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-attack-notifications)** | Provides proactive hunting and prioritization to help identify and respond to the most critical threats. |

### Vulnerability management

Continuously assess vulnerabilities, misconfigurations, and security posture to reduce risk exposure and prioritize remediation.

| Capability | Description |
| --- | --- |
| **[Vulnerability management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)** | Offers risk-based vulnerability management with intelligent prioritization, remediation, and tracking to help you manage and secure your Windows devices. |
| **[Exposure score](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-exposure-score)** | Provides a comprehensive view of your organization's risk exposure. |
| **[Security recommendations](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-recommendation)** | Provides actionable guidance to reduce endpoint risk. |
| **[Remediation tracking](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-remediation)** | Tracks remediation activities and exposure reduction. |
| **[Software inventory](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-software-inventory)** | Provides visibility into installed software on your Windows devices. |
| **[Microsoft Secure Score for Devices](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-microsoft-secure-score-devices)** | Assesses security posture and provides actions to improve overall security. |

### Automated investigation and response

When alerts fire, automated investigation and response \(AIR\) runs automated playbooks to determine scope, collect evidence, and apply remediation actions.

| Capability | Description |
| --- | --- |
| **[Automated investigation and response \(AIR\)](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations)** | Correlates alerts into incidents, runs investigation playbooks, and applies remediation actions such as quarantining files or isolating devices. |

### Device and network discovery

Unmanaged devices represent blind spots that attackers can exploit. Discovery helps you identify them and bring them under management.

| Capability | Description |
| --- | --- |
| **[Endpoint and network device discovery](https://learn.microsoft.com/en-us/defender-endpoint/device-discovery)** | Uses passive network monitoring and active probes to identify unmanaged endpoints, network devices, and IoT devices on the corporate network. |

## Streamlined management and operations

Microsoft Defender for Endpoint on Windows provides flexible deployment and centralized management capabilities designed to simplify configuration, monitoring, and integration with other security tools in Windows environments.

| Capability | Description |
| --- | --- |
| **[Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/protect/advanced-threat-protection) integration** | Integrates with your existing management tools, including Intune and [Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp). |
| **[Security settings management](https://learn.microsoft.com/en-us/intune/intune-service/protect/mde-security-integration)** | Lets you manage security policies directly from the Microsoft Defender portal. |
| **[Management APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/management-apis)** | Provides programmatic access to manage devices, configure policies, query vulnerability data, and retrieve threat intelligence at scale. |
| **[Partner integrations](https://learn.microsoft.com/en-us/defender-endpoint/partner-integration)** | Enables integration with Microsoft and non-Microsoft security solutions. |

## Seamless integration and extensibility

Microsoft Defender for Endpoint on Windows integrates with existing security tools and workflows, extending into the broader Microsoft Defender ecosystem for unified visibility and coordinated security operations.

| Capability | Description |
| --- | --- |
| **Lightweight behavioral sensor** | Built into the operating system, ensuring stable and durable performance. |
| **[API integration](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)** | Enables custom integrations, automation workflows, and third-party tool connectivity through the Defender APIs. |
| **SIEM connectors** | Enables connectivity with SIEM solutions for centralized monitoring and automated response. |
| **[Power BI support](https://learn.microsoft.com/en-us/defender-endpoint/api/api-power-bi)** | Extends visibility through Power BI reporting and role-based access control \(RBAC\). |

Tip

For a detailed comparison of supported features for all Defender for Endpoint platforms \(Windows, macOS, and Linux\), see [Defender for Endpoint capabilities](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint#defender-for-endpoint-capabilities).

## Antivirus solution compatibility

The Microsoft Defender for Endpoint agent depends on Microsoft Defender Antivirus for some capabilities, such as file scanning. For optimal protection, configure [security intelligence updates](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates#security-intelligence-updates) and [platform updates](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-releases#microsoft-defender-antivirus-releases) for onboarded devices, whether Microsoft Defender Antivirus is the active antimalware solution or not.

Important

Endpoint detection and response \(EDR\) in Microsoft Defender for Endpoint doesn't adhere to the Microsoft Defender Antivirus Exclusions settings.

When an onboarded device uses a non-Microsoft antimalware client, Microsoft Defender Antivirus runs in [passive mode](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility), continues to receive updates, and `msmpeng.exe` remains running. In passive mode, Microsoft Defender Antivirus doesn't perform real-time protection scans, scheduled scans, or on-demand scans, and it doesn't replace the non-Microsoft antimalware client. The Microsoft Defender Antivirus user interface is disabled, and users can't run on-demand scans or configure most options \(for example, Attack Surface Reduction \(ASR\) rules, Network Protection, Indicators, Web Content Filtering, and Controlled Folder Access\).

For more information, see [Manage Microsoft Defender Antivirus updates and apply baselines](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates) and [Microsoft Defender Antivirus compatibility](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility).

## What's new in the latest release

To learn what’s new in endpoint security, see the latest updates in [What's new in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/whats-new-in-microsoft-defender-endpoint).

To learn about the latest Windows updates, see [What's new in Microsoft Defender for Endpoint on Windows](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-releases#windows-releases).

## Related content

- [Review the minimum requirements for Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements)
- [Onboard devices and configure capabilities](https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure)
- [Configure Defender for Endpoint security settings](https://learn.microsoft.com/en-us/intune/intune-service/protect/mde-security-integration)
