<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/remove-apps-config -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# Device action: remove apps and configurations

Use the *remove apps and configurations* action in Intune to uninstall apps and remove configuration profiles from a device. This action is useful for troubleshooting or temporarily removing settings that might be causing issues.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated \(COSU\)
> - Android Enterprise corporate-owned fully managed \(COBO\)
> - Android Enterprise corporate-owned work profile \(COPE\)
> - iOS/iPadOS

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, at a minimum, use an account that has one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Change assignments**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

#### Admin permissions and scope tags for Remove apps and configurations

Admins can use the **Remove apps and configurations** action to:

- Select and remove assigned apps and configuration profiles from a device.
- Restore previously removed apps and configuration profiles.

##### Scope tags

Scope tags limit which apps and configurations an admin can view and manage. The visibility is based on the scope tag assignments defined in the admin's role. For more information, see [Use role-based access control and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

## Supported apps and configuration profiles

this action supports the following items:

- **Applications**: Any Intune-delivered app on supported device platforms.

- **Configuration profiles**: Intune-delivered profiles, including:

  - Settings catalog: All
  - Custom
  - Devices features
  - Device restrictions
  - Email
  - PKCS certificate
  - PKCS import certificate
  - SCEP certificate
  - Trusted certificate
  - VPN
  - Wi-Fi

Note

DDM-based policies are not supported for this device action.

- **Configuration profiles**: Intune-delivered profiles, including:

  - Device restrictions
  - PKCS certificate
  - PKCS import certificate
  - SCEP certificate
  - Trusted certificate
  - VPN
  - Wi-Fi

## How to remove apps and configuration from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Remove data** > **Remove apps and configurations**.

[![Remove apps and configuration](https://learn.microsoft.com/en-us/intune/device-management/actions/media/remove-apps-config/remove-apps-config.png)](https://learn.microsoft.com/en-us/intune/device-management/actions/media/remove-apps-config/remove-apps-config.png#lightbox)

1. Select **+ Add**, then select the type of item to remove; **Configuration Item** or **App**.
2. A list of applicable items is displayed with its current state on the device. Select an item to remove, and then use **Select**.
3. The list of selected items is displayed for review; add or delete using the check boxes and header controls. When satisfied with the item list, select **Next**.
4. The **Review + Remove** page is displayed for review, when ready to initiate the remove action, select **Remove**.
5. After the action is initiated, you're redirected to the **Monitor and restore** page. The **Remove** action is initiated for devices that are powered and actively connected to an internet-enabled network; the selected items are removed as soon as possible.

Important

Removal of items such as Wi-Fi, VPN, and Certificates could impact device connectivity, if the items are ultimately used for connectivity to the Intune service. **Remove apps and configurations** is intended to be used interactively by Intune admins working with impacted users. If connectivity is lost, users might need to take actions on devices to restore connectivity; connect the device to a guest or alternate Wi-Fi or cellular network.

## Monitoring the device action remove apps and configuration

After you initiate the *Remove apps and configurations* action on a device, the **Status** column of the **Overview** page displays the status of the action. The status is updated as the action progresses.

You can manually restore the removed items using the **Restore** action. If no restore is initiated, Intune automatically reapplies the apps and configurations within 8-24 hours to ensure the device remains aligned with assignment intent.

[![Monitor the device action - Remove apps and configuration](https://learn.microsoft.com/en-us/intune/device-management/actions/media/remove-apps-config/remove-apps-config-monitor.png)](https://learn.microsoft.com/en-us/intune/device-management/actions/media/remove-apps-config/remove-apps-config-monitor.png#lightbox)

Important

Removed items are reflected with an assignment status of *Removed*, but this status is not included in the count. Removals are temporary and will be automatically restored to devices. The total count is not inclusive of devices with an active *Removed* status.

The monitoring page displays the following information:

- Available actions
  | Action | Description |
  | --- | --- |
  | **Add** | Add more items for removal |
  | **Refresh** | Refresh the list and track progression of remove/ restore. |
  | **Columns** | Enable/disable columns. |
  | **Restore all** | Restore all removed items in the list. When you select the **Restore all** button in the table header, a confirmation box is displayed. When ready, select **Restore all** initiate restoration of all Removed apps or configurations to the device. |
  | **Restore select items** | Restore selected items in the list. Select one or more items using the selection check box and then select the **Restore** button to initiate the restore of selected items or Configurations to the device. |
  | **Last refreshed on** | Shows the timestamp of when the list was last refreshed. |
- Display columns:
  | Column name | Description |
  | --- | --- |
  | **Name** | Application or policy name |
  | **Item type** | Application or policy type |
  | **Action** | Current action for the item |
  | **Started** | Date/time stamp when the action was initiated |
  | **Status** | - **In Progress**: remove attempt to device initiated, pending response  <br>- **Removed**: item removed from device  <br>- **Restored**: item restored to device  <br>- **Error**: action resulted in error, see status details |
  | **Status time** | Date/timestamp when the status was updated |
  | **Status detail** | When populated, shows more details for the status |

## Reference links

- Microsoft Graph API: [changeAssignments action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-changeassignments) in the Microsoft Graph API documentation.
