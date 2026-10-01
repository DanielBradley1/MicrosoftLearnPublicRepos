<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-asr -->
<!-- Sitemap-Last-Modified: 2026-06-25 -->

# Attack surface reduction in Microsoft Defender for Business

*Attack surfaces* are all the places and ways the network and devices in your organization are vulnerable to cyberattack. For example:

- Unsecured devices.
- Unrestricted access to URLs on company devices.
- Unrestricted running of apps or scripts on company devices.

To help protect your network and devices, Microsoft Defender for Business includes several attack surface reduction capabilities. These capabilities include *attack surface reduction \(ASR\) rules* as described in the following table:

| Capability | Description |
| --- | --- |
| **[Attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview)** | Prevent specific actions commonly associated with malicious activity from running on Windows devices. |
| **[Controlled folder access \(CFA\)](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview)** | Allow only trusted apps to access protected folders on Windows devices. Think of this capability as ransomware mitigation. |
| **[Firewall protection](https://learn.microsoft.com/en-us/defender-business/mdb-firewall)** | Determines which network traffic can flow to or from your organization's devices. |
| **[Network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection)** | Prevent users from accessing dangerous domains through applications on their Windows and Mac devices. Network protection is also a key component of [web content filtering](https://learn.microsoft.com/en-us/defender-business/mdb-web-content-filtering). |
| **[Web protection](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-overview)** | Integrates with web browsers and works with network protection to protect against web threats and unwanted content. Web protection includes [web threat protection](https://learn.microsoft.com/en-us/defender-endpoint/web-threat-protection), [web content filtering](https://learn.microsoft.com/en-us/defender-endpoint/web-content-filtering), and [custom indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview). |

## Configure attack surface reduction features

Note

Microsoft 365 Business Premium includes Microsoft Intune Plan 1, which is the recommended method to configure and deploy security features on devices. Standalone Defender for Business doesn't include Intune, so you need to use another configuration method, for example, Group Policy or PowerShell locally on devices.

- **Attack surface reduction \(ASR\) rules**: For more information, see [Deployment and configuration methods for ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#deployment-and-configuration-methods-for-asr-rules) and [ASR rules deployment guide](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment).
- **Controlled folder access \(CFA\)**: For more information, see [Deployment and configuration methods for CFA](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#deployment-and-configuration-methods-for-cfa).
- **Firewall protection**: Enabled by default when devices are onboarded to Defender for Business and [firewall policies in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-firewall) are applied.
- **Network protection**: Enabled by default when devices are onboarded to Defender for Business and [next-generation protection policies](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection) are applied. Default policies are configured with the recommended security settings.
- **Web protection**: [Set up web content filtering in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-web-content-filtering).

## Monitor attack surface reduction features

You can monitor how attack surface reduction features are working in your organization by using the following reports in the Microsoft Defender portal:

- **ASR rules**: [Attack surface reduction \(ASR\) rules report](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-report)
- **Controlled folder access**: [Monitor controlled folder access activity](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-monitor)
- **Network and web protection**: [Web protection monitoring report](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-monitoring)
- **Firewall**: [Host firewall reporting](https://learn.microsoft.com/en-us/defender-endpoint/host-firewall-reporting)

## Related content

- [Review settings for advanced features and the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-business/mdb-portal-advanced-feature-settings)
- [Use your vulnerability management dashboard](https://learn.microsoft.com/en-us/defender-business/mdb-view-tvm-dashboard)
- [View and manage incidents](https://learn.microsoft.com/en-us/defender-business/mdb-view-manage-incidents)
- [View reports](https://learn.microsoft.com/en-us/defender-business/mdb-reports)
