<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/identify-directory-synchronization-errors?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-07-17 -->

# View directory synchronization errors in Microsoft 365

You can view directory synchronization errors in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). Only the User object errors are displayed. To view errors with PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## View directory synchronization errors in the Microsoft 365 admin center

To view any errors in the Microsoft 365 admin center:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with a Hybrid Identity Administrator account.
2. On the **Home** page, you'll see the **User management** card.

   ![The User management card in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/060006e9-de61-49d5-8979-e77cda198e71.png?view=o365-worldwide)
3. On the card, choose **Sync errors** under **Microsoft Entra Connect** to see the errors on the **Directory sync errors** page.

   ![An example of the Directory sync errors page.](https://learn.microsoft.com/en-us/microsoft-365/media/882094a3-80d3-4aae-b90b-78b27047974c.png?view=o365-worldwide)
4. Choose any of the errors to display the details pane with information about the error and tips on how to fix it.

   ![Example of the details of a directory sync error.](https://learn.microsoft.com/en-us/microsoft-365/media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png?view=o365-worldwide)

After viewing, see [fixing problems with directory synchronization for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/fix-problems-with-directory-synchronization?view=o365-worldwide) to correct any identified issues.
