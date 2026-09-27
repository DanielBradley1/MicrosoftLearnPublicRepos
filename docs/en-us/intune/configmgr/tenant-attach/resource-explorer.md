<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/resource-explorer -->
<!-- Sitemap-Last-Modified: 2023-02-22 -->

# Tenant attach: Resource explorer in the admin center

*Applies to: Configuration Manager \(current branch\)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. From the Microsoft Endpoint Management admin center, you can view hardware inventory for uploaded Configuration Manager devices by using resource explorer.

[![Resource explorer in Microsoft Intune admin center](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6479284-resource-explorer.png)](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6479284-resource-explorer.png#lightbox)

## Prerequisites

The following items are required to use resource explorer from the admin center:

- All of the prerequisites for [Tenant attach: ConfigMgr client details](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/client-details).
- A supported version of Configuration Manager version and the corresponding version of the console installed.

  - Historical inventory data requires Configuration Manager version 2103, or later.

- Upgrade the target devices to the latest version of the Configuration Manager client.

## Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Read Resource** permission for the device's **Collection** in Configuration Manager.
- An [Intune role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview) assigned to the user

## Launch resource explorer

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions).
4. Select **Resource explorer** to view hardware inventory.
5. Search for or select a class to retrieve information from the client.

   [![Resource explorer with the motherboard class selected](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6479284-resource-explorer-details.png)](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6479284-resource-explorer-details.png#lightbox)

## Historical inventory data in resource explorer

*Applies to Configuration Manager 2103, or later*

Resource explorer can display a historical view of the device inventory in the Microsoft Intune admin center. When troubleshooting, having historical inventory data can provide valuable information about changes to the device.

1. From the Microsoft Intune admin center, select **Resource explorer**.
2. Select a class.
3. Enter a custom date in the date time picker to get historical inventory data.

[![Screenshot of choosing a date from Resource explorer in the Microsoft Intune admin center](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/9546584-resource-explorer-historical-inventory.png)](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/9546584-resource-explorer-historical-inventory.png#lightbox)

## Close resource explorer

To close resource explorer and return to the device information, use the `X` icon in the top right of resource explorer.

[![Close resource explorer with the x icon in Microsoft Intune admin center](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6479284-close-resource-explorer.png)](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6479284-close-resource-explorer.png#lightbox)

## Next steps

[Troubleshoot resource explorer](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot-resource-explorer)
