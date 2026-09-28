<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-reprovision-cloudpc?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-01-20 -->

# Reprovision a Windows 365 Cloud PC in Microsoft 365 Lighthouse

Microsoft 365 Lighthouse supports reprovisioning of Cloud PCs that have a provisioning policy. You may need to reprovision a device for a new user or if the device isn't working properly. When a reprovision is triggered, the Cloud PC is deleted and re-created as a new Cloud PC. All user data, applications, and customizations are deleted.

## Before you begin

You must hold the Cloud PC Administrator role in Microsoft Intune to reprovision a Windows 365 Cloud PC in Lighthouse.

## Reprovision a Windows 365 Cloud PC

1. In the left navigation pane in [Lighthouse](https://go.microsoft.com/fwlink/p/?linkid=2168110), select **Devices** > **Windows 365**.
2. Select the **All Cloud PCs** tab.
3. From the **Filters** dropdown list, select license type.
4. From the filtered list, select a device.
5. In the device details pane, select **Reprovision**.
6. In the confirmation dialog, select **Yes, reprovision this Cloud PC**, and then select **Reprovision**.

Note

The current user of the Cloud PC is immediately signed out and all user data is removed.

## Check the device action status

1. In the left navigation pane in [Lighthouse](https://go.microsoft.com/fwlink/p/?linkid=2168110), select **Devices** > **Windows 365**.
2. Select the **All Cloud PCs** tab.
3. From the list of devices, select a device.
4. In the device details pane, select the **Device action status** tab.

The tab displays the status of the most recent action queued for the selected device, including the action type, status, and timestamp.

## Related content

[Provisioning Overview](https://learn.microsoft.com/en-us/windows-365/enterprise/provisioning) \(article\)  
[Edit provisioning policies](https://learn.microsoft.com/en-us/windows-365/enterprise/edit-provisioning-policy) \(article\)
