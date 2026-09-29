<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/threat-analytics-indicators -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Get access to IOCs in threat analytics in Microsoft Defender \(preview\)

**Applies to:**

- Microsoft Defender XDR

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Each [threat analytics report](https://learn.microsoft.com/en-us/defender-xdr/threat-analytics) includes an *indicators* section that lists all indicators of compromise \(IOCs\) associated with the threat. Microsoft researchers update these IOCs in real time as they find new evidence related to the threat. These IOCs and their real-time updates help your security operations center \(SOC\) and threat intelligence analysts with remediation and proactive hunting. The list also retains expired IOCs, so you can investigate past threats and understand their impact in your environment.

Because IOCs are valuable information in the context of prevalent threats and threat campaigns, only verified Microsoft Defender customers can access them. This article explains how you can check if you have access to the indicators section and how you unlock it if you don't.

## View IOCs in threat analytics

To access the indicators section, go to the **Threat analytics** page, open the report about the tracked threat, and select the **Indicators** tab.

If you're a verified customer, you can immediately see the list of IOCs displayed in the **Indicators** tab.

[![Screenshot of the Indicators tab in a threat analytics report.](https://learn.microsoft.com/en-us/defender-xdr/media/ta-indicators/indicators-full.png)](https://learn.microsoft.com/en-us/defender-xdr/media/ta-indicators/indicators-full.png#lightbox)

If you're not a verified customer, the **Indicators** tab displays a message that access to indicators is restricted.

[![Screenshot of a restricted Indicators tab in a threat analytics report.](https://learn.microsoft.com/en-us/defender-xdr/media/threat-analytics-indicators/indicators-restricted.png)](https://learn.microsoft.com/en-us/defender-xdr/media/threat-analytics-indicators/indicators-restricted.png#lightbox)

## Unlock access to indicators

To unlock the **Indicators** tab, complete these steps:

1. On the **Indicators** page, select **Complete Verification**.
2. Provide the required information and any supporting documents.
3. Select **Submit verification request**.

Verification can take an hour or more. After it completes, refresh the **Indicators** tab. If your tenant is validated, the list of IOCs appears.

Note

In some cases, we might require additional information during the verification process. We communicate these requirements through email.

If you still don't have access to the **Indicators** section after going through the verification process, contact the email address displayed on the **Indicators** page.

[![Screenshot of a restricted Indicators tab in a threat analytics report showing the email address to contact.](https://learn.microsoft.com/en-us/defender-xdr/media/threat-analytics-indicators/indicators-contact.png)](https://learn.microsoft.com/en-us/defender-xdr/media/threat-analytics-indicators/indicators-contact.png#lightbox)

## Related content

- [Threat analytics overview](https://learn.microsoft.com/en-us/defender-xdr/threat-analytics)
- [Understand the analyst report section](https://learn.microsoft.com/en-us/defender-xdr/threat-analytics-analyst-reports)
- [Proactively find threats with advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
