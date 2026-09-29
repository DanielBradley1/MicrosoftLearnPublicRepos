<!-- Source: https://learn.microsoft.com/en-us/defender-for-iot/manage-sites -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Manage sites in Microsoft Defender for IoT

Microsoft Defender for IoT in the Microsoft Defender portal includes the **Site security** page, which allows you to see the up-to-date security state of your production sites. Learn more about the [site security benefits and use cases](https://learn.microsoft.com/en-us/defender-for-iot/site-security-overview) or how to [monitor site security](https://learn.microsoft.com/en-us/defender-for-iot/monitor-site-security).

When you manage a site, you might need to edit or delete the site information listed in the **Site security** page. Use the **Site security** page to update device site associations, edit or delete a site, and add a device group in the Microsoft Defender portal.

Important

This article discusses Microsoft Defender for IoT in the Defender portal \(Preview\).

Some features are not yet available in the Defender portal. If you're interested in these features, or you're an existing customer working on the Azure portal, see the [Defender for IoT on Azure documentation](https://learn.microsoft.com/en-us/azure/defender-for-iot/organizations/overview).

Learn more about the [Defender for IoT management portals](https://learn.microsoft.com/en-us/defender-for-iot/microsoft-defender-iot#what-are-the-different-management-portals-for-microsoft-defender-for-iot).

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Manually update device site association

Security admininstrators can manually assign or modify the site location for a device. Manually assigning a site overrides the automatic site association created when making the site.

To quickly update a group of devices, select multiple devices from the inventory and set the site for all of the selected devices simulataneously.

**To change the site associated with a device**:

1. Select **Assets -> Devices** to open the **Device Inventory**.
2. Select the device, or group of devices, to update. A list of action buttons appear at the top of the Device Inventory table.
3. Select **Set site**. The **Set site** pane opens.

   [![Screenshot of the set site button in the device inventory table for changing the site location setting](https://learn.microsoft.com/en-us/defender-for-iot/media/manage-sites/set-site-from-inventory-boxed.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/manage-sites/set-site-from-inventory-boxed.png#lightbox)
4. In **Set site manually**, open the **Select site** drop down list and select the site to associate with this device. If you want to leave a device unassociated with a specific site, select **Unassigned**.

   [![Screenshot of the set site manually drop down list for changing the site location setting](https://learn.microsoft.com/en-us/defender-for-iot/media/manage-sites/device-set-site-manually.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/manage-sites/device-set-site-manually.png#lightbox)
5. Select **Save and close**.
6. The Set site confirmation box appears. Select **Confirm** to finalize the change. Finalizing the change prevents automatic site reassignment based on existing site security rules. The manual site assignment remains until the device is reset manually.

Note

For managing an entire site, instead of manually changing each individual device to a new site, it is recommended to go to **Site security** and use the **Edit site** wizard to more efficiently manage the site and the devices associated to it. For more information, see [Monitor site security](https://learn.microsoft.com/en-us/defender-for-iot/monitor-site-security).

## Edit or delete a site

To edit or delete a site:

1. In the [Microsoft Defender portal](https://security.microsoft.com/machines) menu, select **Operational technology** > **Site security**.
2. Select the ellipsis \(![](https://learn.microsoft.com/en-us/defender-for-iot/media/manage-sites/menu-ellipsis.png) \) to the right of the site name.
3. Select one of the following:

   - Select **Edit site** to open the **Site details** pane, where you can make changes to the site. For more information, see [Site details](https://learn.microsoft.com/en-us/defender-for-iot/set-up-sites).
   - Select **Delete site** to remove a site from the site list.

     Warning

     Deleting a site removes all site-related information for the associated devices. This action can't be undone.

## Add a device group to a site

You can create a device group based on a site location to restrict access to a specific site or group of sites, and verify that the correct users have access to your site.

You can set up a device group at different stages:

- To set up a device group as part of the site setup, see [Add a device group](https://learn.microsoft.com/en-us/defender-for-iot/set-up-sites#add-device-group).
- To set up a device group after you set up a site, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

To get the full benefit of a site-based device group, you might need to create roles and permission settings. For more information, see:

- [Role based access control in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/rbac)
- [Create and manage roles in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/user-roles)
