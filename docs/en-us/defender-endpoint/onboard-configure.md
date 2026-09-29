<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure -->
<!-- Sitemap-Last-Modified: 2025-09-29 -->

# Configure Microsoft Defender for Endpoint capabilities

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

In this step, you're ready to configure Microsoft Defender for Endpoint capabilities.

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

## Configure capabilities

In many cases, organizations have existing endpoint security products in place. The bare minimum being an antivirus solution, but in some cases, an organization might have existing endpoint detection and response solution.

It's common that Defender for Endpoint needs to exist along side these existing endpoint security products either indefinitely or during a cutover period. Fortunately, Defender for Endpoint and the endpoint security suite is modular and can be adopted in a systematic approach.

Onboarding devices effectively enables the endpoint detection and response capability of Microsoft Defender for Endpoint. After onboarding the devices, you'll then need to configure the other capabilities of the service. The following table lists the capabilities you can configure to get the best protection for your environment and the order Microsoft recommends for how the endpoint security suite should be enabled.

| Capability | Description | Adoption Order Rank |
| --- | --- | --- |
| [Endpoint Detection & Response \(EDR\)](https://learn.microsoft.com/en-us/defender-endpoint/overview-endpoint-detection-response) | Defender for Endpoint endpoint detection and response capabilities provide advanced attack detections that are near real-time and actionable. Security analysts can prioritize alerts effectively, gain visibility into the full scope of a breach, and take response actions to remediate threats. | 1 |
| [Configure Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-prerequisites) | Defender Vulnerability Management is a component of Microsoft Defender for Endpoint, and provides both security administrators and security operations teams with unique value, including:  <br>  <br>- Real-time endpoint detection and response \(EDR\) insights correlated with endpoint vulnerabilities.  <br>  <br>- Invaluable device vulnerability context during incident investigations.  <br>  <br>- Built-in remediation processes through Microsoft Intune and Microsoft System Center Configuration Manager. | 2 |
| [Configure Next-generation protection \(NGP\)](https://learn.microsoft.com/en-us/defender-endpoint/configure-microsoft-defender-antivirus-features) | Microsoft Defender Antivirus is a built-in antimalware solution that provides next-generation protection for desktops, portable computers, and servers. Microsoft Defender Antivirus includes:  <br>  <br>-Cloud-delivered protection for near-instant detection and blocking of new and emerging threats. Along with machine learning and the Intelligent Security Graph, cloud-delivered protection is part of the next-gen technologies that power Microsoft Defender Antivirus.  <br>  <br>- Always-on scanning using advanced file and process behavior monitoring and other heuristics \(also known as "real-time protection"\).  <br>  <br>- Dedicated protection updates based on machine learning, human and automated big-data analysis, and in-depth threat resistance research. | 3 |
| [Configure attack surface reduction](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-overview) | Attack surface reduction capabilities in Microsoft Defender for Endpoint help protect the devices and applications in the organization from new and emerging threats. | 4 |
| [Configure Auto Investigation & Remediation \(AIR\) capabilities](https://learn.microsoft.com/en-us/defender-endpoint/configure-automated-investigations-remediation) | Microsoft Defender for Endpoint uses Automated investigations to significantly reduce the volume of alerts that need to be investigated individually. The Automated investigation feature uses various inspection algorithms, and processes used by analysts \(such as playbooks\) to examine alerts and take immediate remediation action to resolve breaches. AIR significantly reduces alert volume, allowing security operations experts to focus on more sophisticated threats and other high value initiatives. | Not applicable |
| [Activate Microsoft Defender for Identity capabilities directly on a domain controller](https://learn.microsoft.com/en-us/defender-for-identity/deploy/activate-capabilities) | Microsoft Defender for Identity customers, who've already onboarded their domain controllers to Defender for Endpoint, can activate Microsoft Defender for Identity capabilities directly on a domain controller instead of using a Microsoft Defender for Identity sensor. | Not applicable |
| [Configure Microsoft Defender Experts capabilities](https://learn.microsoft.com/en-us/defender-xdr/defender-experts-for-hunting) | Microsoft Experts is a managed hunting service that provides Security Operation Centers \(SOCs\) with expert level monitoring and analysis to help them ensure that critical threats in their unique environments don't get missed. | Not applicable |

For more information, see [Supported Microsoft Defender for Endpoint capabilities by platform](https://learn.microsoft.com/en-us/defender-endpoint/supported-capabilities-by-platform).
