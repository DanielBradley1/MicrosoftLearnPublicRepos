<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/posture-overview -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# SaaS security posture management \(SSPM\) overview

One of the pillars of Microsoft Defender for Cloud Apps is SaaS security posture management \(SSPM\). SSPM offers detailed visibility into the security state of your software as a service \(SaaS\) applications. It also provides actionable guidance to help you strengthen your security posture efficiently.

Defender for Cloud Apps provides security configuration assessments to help you identify and mitigate potential risks in your SaaS application environments. These recommendations appear in [Microsoft Security Exposure Management](https://learn.microsoft.com/en-us/security-exposure-management/microsoft-security-exposure-management) after you connect the SaaS application by using an app connector in Defender for Cloud Apps.

Additionally, Defender for Cloud Apps includes OAuth applications in both the Attack Path and Attack Surface Map experiences. To learn more about investigating OAuth application attack paths, see [How to investigate OAuth application attack paths in Defender for Cloud Apps \(Preview\)](https://learn.microsoft.com/en-us/defender-cloud-apps/attack-paths)

Note

Microsoft Security Exposure Management data and capabilities are currently unavailable in US government clouds: GCC, GCC High, and DoD. For US government clouds \(GCC, GCC High, and DoD\), we recommend consuming SaaS security posture recommendations via [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/tvm-security-recommendation).

The following screenshot shows Secure Score recommendations for a Salesforce app:

[![Screenshot of Salesforce recommendations in Secure Score.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/security-saas-sspm-in-secure-score-salesforce-filter.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/security-saas-sspm-in-secure-score-salesforce-filter.png#lightbox)

## Prerequisites

Before you turn on SaaS security recommendations, make sure the following prerequisites are met:

- Your organization must have Microsoft Defender for Cloud Apps licenses.
- Your app must be connected to Defender for Cloud Apps. For information about connecting and about which of the app connectors provide security recommendations, see [Connect apps to get visibility and control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps).

## Turn on SaaS security recommendations

To ensure that your application connector is set to show data in Microsoft Security Exposure Management, follow these steps:

1. In Microsoft Defender XDR, select **Settings** > **Cloud Apps** > **Connected apps** > **App Connectors**.
2. Use the filter to locate the application where you want to turn on security recommendations.
3. Open the instance drawer and note whether **Security recommendations** is turned on or off. In the following screenshot, **Security recommendations** is turned on.

   [![Screenshot of an app instance where Secure Score recommendations are turned on.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/posture-overview/screenshot-of-an-instance-where-secure-score-recommendations-are-turned-on.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/posture-overview/screenshot-of-an-instance-where-secure-score-recommendations-are-turned-on.png#lightbox)

   If the instance is currently set to **Off**, select the ellipsis that denotes the options menu \(**...**\), and then select **Turn on Security recommendations**.

   [![Screenshot that shows the command for turning on security recommendations.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/posture-overview/screenshot-of-the-turn-on-secure-score-or-exposure-management-recommendations-option.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/posture-overview/screenshot-of-the-turn-on-secure-score-or-exposure-management-recommendations-option.png#lightbox)

   Note

   If you have multiple instances of the same app, you can send security recommendations for each instance separately. Security recommendations for the selected instance are added to Microsoft Security Exposure Management in addition to the current recommendations.

Security recommendations appear automatically in Microsoft Security Exposure Management. Recommendations are based on Microsoft benchmarks, and they might take time to update.

In [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score), filter the **Recommended actions** tab by product to view any recommended actions. If you have multiple instances of an app, you can choose to filter recommendations from specific instances only. The following screenshot shows filter options for specific app instances:

[![Screenshot of a Secure Score filter that shows multiple instances of an app.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/secure-score-filter.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/secure-score-filter.png#lightbox)

Select a recommendation, and then select the **Implementation** tab on the details pane for a step-by-step remediation guide.

For more information, see [Assess your security posture with Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score-improvement-actions).

## Manage your organization's SaaS security posture

To effectively manage your organization's SaaS security posture, we recommend beginning with the [SaaS Security Initiative](https://learn.microsoft.com/en-us/defender-cloud-apps/saas-security-initiative). The SaaS Security Initiative consolidates best practices and measurable metrics specifically for securing SaaS applications, so that you can prioritize and address the most impactful recommendations for SaaS environments. The following screenshot shows security metrics from the SaaS Security Initiative:

[![Screenshot of metrics from the SaaS Security Initiative.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/posture-overview/screenshot-of-the-saas-security-initiative-home-page.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/posture-overview/screenshot-of-the-saas-security-initiative-home-page.png#lightbox)

You can also find various SSPM recommendations under other initiatives:

- CIS Microsoft 365 Foundations Benchmark
- Ransomware Protection
- Identity Security
- Business Email Compromise \(financial fraud\)
- Zero Trust \(foundational\)

### Investigate attack paths for OAuth apps \(Preview\)

After configuring SaaS posture recommendations in Defender for Cloud Apps, you can use the attack paths capability to expand your investigation. Attack paths show how an attacker might move laterally from a vulnerable entry point, through an OAuth application, to gain high privileges in your Microsoft 365 SaaS environment. Attack path visibility helps you investigate potential threats and take steps to remediate them. To learn more, see [How to investigate OAuth application attack paths in Defender for Cloud Apps \(Preview\)](https://learn.microsoft.com/en-us/defender-cloud-apps/attack-paths)

## Next steps

[Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
