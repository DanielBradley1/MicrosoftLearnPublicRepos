<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-change-cloud-pc-account-type?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-01-20 -->

# Change a Windows 365 Business Cloud PC account type in Microsoft 365 Lighthouse

Managed Service Provider \(MSP\) technicians may set the account type for a Business Cloud PC or make changes to an existing account type. The following account types are available:

- **Standard user \(Recommended\)** - Standard user accounts have permission to install software only from the Microsoft Store.
- **Local administrator** - Local administrator accounts have permission to install any software and make changes to any part of the operating system. Select this account type only when needed, since malware may use administrator permissions to infect or damage files.

Note

You can set or change the account type only for Cloud PCs with a Business license. You can't change the account type for Cloud PCs with an Enterprise license.

## Before you begin

You must hold either the Cloud PC Administrator \(recommended\) or Windows 365 Administrator role in Microsoft Intune to set or change a Windows 365 Business Cloud PC account type in Lighthouse.

Caution

To help keep your organization secure, Microsoft recommends that you use roles with the minimum level of permissions needed to perform a job.

## Set or change a Windows 365 Business Cloud PC account type

1. In the left navigation pane in [Lighthouse](https://go.microsoft.com/fwlink/p/?linkid=2168110), select **Devices** > **Windows 365**.
2. Select the **All Cloud PCs** tab.
3. Use the colored count-annotation bar to drill into Cloud PCs that have a **Provisioned** status.
4. From the **Filters** dropdown menu, select the **Business** license type to see a list of all Cloud PCs with a Business license within your customer tenants.
5. From the list of Cloud PCs, select the Cloud PC for which you want to change the account type.
6. In the Cloud PC details pane, select **Change account type**.
7. In the **Change Cloud PC account type** pane, select the account type for the Cloud PC, and then select **Save**.

## Next steps

Once the update is applied, the assigned user of the Cloud PC will need to sign back into the Cloud PC or restart their device. It may take several minutes for the new changes to appear in Microsoft 365 Lighthouse. The Cloud PC Administrator can also remotely restart the Cloud PC, but the user may lose any unsaved data.

## Related content

[Cloud PC role-based access control](https://learn.microsoft.com/en-us/windows-365/enterprise/role-based-access) \(article\)  
[Overview of the Windows 365 \(Cloud PCs\) page in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-win365-page-overview?view=o365-worldwide) \(article\)  
[Reprovision a Windows 365 Cloud PC in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-reprovision-cloudpc?view=o365-worldwide) \(article\)
