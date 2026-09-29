<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/utilize-microsoft-defender-for-office-365-in-sharepoint-online -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Use Microsoft Defender for Office 365 with SharePoint

SharePoint in Microsoft 365 is a widely used user collaboration and file storage tool. The following steps help reduce the attack surface area in SharePoint and that help keep this collaboration tool in your organization secure. However, it's important to note there's a balance to strike between security and productivity, and not all these steps might be relevant for your organizational risk profile. Take a look, test, and maintain that balance.

## Prerequisites

- Microsoft Defender for Office 365 Plan 1
- Sufficient permissions \(SharePoint administrator/security administrator\)
- Microsoft SharePoint \(part of Microsoft 365\)
- [SharePoint Online Management Shell](https://learn.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) installed and configured
- Five to 10 minutes to perform these steps

## Turn on Microsoft Defender for Office 365 in SharePoint

If you're licensed for Microsoft Defender for Office 365 **\(free 90-day evaluation available at aka.ms/trymdo\)**, you can ensure seamless protection from zero day malware and time of click protection within Microsoft Teams.

To learn more, read [Step 1: Use the Microsoft Defender portal to turn on Safe Attachments for SharePoint, OneDrive, and Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-for-spo-odfb-teams-configure#step-1-use-the-microsoft-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams).

1. Sign in to the [security center's safe attachments configuration page](https://security.microsoft.com/safeattachmentv2).
2. Select **Global settings**.
3. Ensure that **Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams** is set to **on**.
4. Select **Save**.

## Stop infected file downloads from SharePoint

By default, users can't open, move, copy, or share malicious files that are detected by Safe Attachments for SharePoint, OneDrive, and Microsoft Teams. However, the *Download* option is still available and should be *disabled*.

To learn more, read [Step 2: \(*Recommended*\) Use SharePoint Online PowerShell to prevent users from downloading malicious files](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-for-spo-odfb-teams-configure#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

1. Open and connect to [SharePoint Online PowerShell](https://learn.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).
2. Run the following command: **Set-SPOTenant -DisallowInfectedFileDownload $true**.

## Related content

For more guidance on securing your environment, see the following resource:

[Policy recommendations for securing SharePoint sites and files](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-identity-device-access-policies-sharepoint)
