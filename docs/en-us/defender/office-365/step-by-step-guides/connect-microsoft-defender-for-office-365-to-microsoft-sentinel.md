<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/connect-microsoft-defender-for-office-365-to-microsoft-sentinel -->
<!-- Sitemap-Last-Modified: 2026-06-18 -->

# Connect Microsoft Defender for Office 365 to Microsoft Sentinel

This article walks you through connecting Microsoft Defender for Office 365 to Microsoft Sentinel by using the Microsoft Defender XDR data connector. This includes incidents and data from the rest of the Microsoft Defender suite.

This integration provides security information and event management \(SIEM\) features with data from other Microsoft 365 sources. You can also sync incidents and alerts, and run advanced hunting queries.

## Prerequisites

Before you begin, make sure you have the following items:

- Microsoft Defender for Office 365 Plan 2 or higher. \(Included in E5 plans\)
- Microsoft Sentinel [Quickstart guide](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard).
- Sufficient permissions \(Security Administrator in Microsoft 365 & Read / Write permissions in Sentinel\).

## Add the Microsoft Defender XDR Connector

Microsoft Defender for Office 365 data is onboarded to Microsoft Sentinel through the Microsoft Defender XDR connector. Follow these steps to add and configure the connector:

1. [Sign in to the Azure portal](https://portal.azure.com) and go to **Microsoft Sentinel**. Pick the workspace to use with Microsoft Defender XDR.
2. Under **Configuration**, select **Data connectors**.
3. Search for **Microsoft Defender XDR** and select the connector.
4. Select **Open Connector Page**.
5. Under **Configuration**, select **Connect incidents & alerts**. Keep **Turn off all Microsoft incident creation rules for these products** selected.
6. In the **Connect events** section, under **Microsoft Defender for Office 365**, select **EmailEvents**, **EmailUrlInfo**, **EmailAttachmentInfo**, and **EmailPostDeliveryEvents**, then select **Apply Changes**. You can also choose tables from other Defender products during this step.

## Next Steps

Admins can now view incidents, alerts, and raw data in Microsoft Sentinel. They can also use *advanced hunting* to explore new and existing data from Microsoft Defender.

## Related content

- [Connect Microsoft Defender data to Microsoft Sentinel \| Microsoft Docs](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender?tabs=MDE)
- [Connect Microsoft Teams to Microsoft Sentinel](https://learn.microsoft.com/en-us/microsoftteams/teams-sentinel-guide)
