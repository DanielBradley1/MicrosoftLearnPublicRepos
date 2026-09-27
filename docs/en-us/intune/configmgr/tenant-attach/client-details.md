<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/client-details -->
<!-- Sitemap-Last-Modified: 2024-04-22 -->

# Tenant attach: ConfigMgr client details in the admin center

*Applies to: Configuration Manager \(current branch\)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. You can see ConfigMgr client details including collections, boundary group membership, and real-time client information for a specific device in the admin center.

## Prerequisites

- All of the prerequisites for [Microsoft Intune tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions) and a tenant attached environment.
- One of the following browsers:

  - Microsoft Edge, version 77 and later
  - Google Chrome

- The user accounts triggering device actions have the following prerequisites:

  - The user account needs to be a synced user object in Microsoft Entra ID \(hybrid identity\). This means that the user is synced to Microsoft Entra ID from Active Directory.

    - For Configuration Manager version 2103, and later:  
      Has been discovered with [Microsoft Entra user discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc) and [Active Directory user discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
    - Starting in Configuration Manager version 2207, you can choose to implement [Intune role-based access control for tenant-attached clients](https://learn.microsoft.com/en-us/intune/configmgr/cloud-attach/use-intune-rbac) to allow cloud-only users access to tenant attached clients

## Permissions

The user account accessing tenant attach features within the Microsoft Intune admin center needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- An [Intune role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview) assigned to the user

Important

The "Enforce Configuration Manager RBAC for cloud console requests that interact with Configuration Manager" check box does not grant permissions to the user to perform cloud console requests that interact with Configuration Manager unless the user is assigned an Intune role.

## View ConfigMgr client details

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions).
4. Select the **Client details**.

   - The primary site updates the following fields once an hour:

     - **Last policy request**
     - **Last active time**
     - **Last management point**.


   [![Client details in Microsoft Intune admin center](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6024387-device-details.png)](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6024387-device-details.png#lightbox)

5. Select the **Collections** to list the client's collections.

   [![Client collections in Microsoft Intune admin center](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6024387-device-collections.png)](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/6024387-device-collections.png#lightbox)

## List a user’s devices based on usage in the troubleshooting portal

The troubleshooting portal in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) allows you to search for a user and view their associated devices. Tenant attached devices that are assigned [user device affinity automatically based on usage](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/link-users-and-devices-with-user-device-affinity#set-up-the-site-to-automatically-create-user-device-affinities) will now be returned when searching for a user.

### Prerequisites for listing a user's device in the troubleshooting portal

- An environment that's tenant attached with uploaded devices
- Install the latest version of the Configuration Manager client
- Target clients with **User and Device Affinity** [client settings](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-settings#user-and-device-affinity) to automatically create the affinities

  - For more information, see [Create user device affinity automatically based on usage](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/link-users-and-devices-with-user-device-affinity#set-up-the-site-to-automatically-create-user-device-affinities).
  -

### View a user's devices

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Troubleshooting + support**.
3. On the **Troubleshoot** page, select **Change user** then search for a user.
4. The **Devices** chart lists the ConfigMgr devices associated with the user.

   - Devices that previously reported affinity will resend their affinity to reflect in the admin center.
   - Devices that aren't already associated with a user will be updated once the affinity threshold has been met and reported.

## Next steps

[Troubleshoot client details](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot-client-details)
