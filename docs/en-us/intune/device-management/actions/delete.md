<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/delete -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Device action: delete

Use the *delete* action in Intune to permanently remove devices that are no longer needed, being repurposed, or missing. This action helps cleanup your device inventory and ensures that unmanaged or obsolete devices no longer appear in the admin center.

Important

A tenant can submit up to 1,000 Delete actions per day. This tenant-wide limit is cumulative across individual device actions, bulk device actions, and Microsoft Graph API requests. The Delete limit applies to Delete requests even when deleting a device triggers a Retire or Wipe command. To request a limit change, [contact Microsoft support](https://learn.microsoft.com/en-us/intune/fundamentals/it-pro-support/get-support-admin-center). For all device action limits, see [Daily tenant limits](https://learn.microsoft.com/en-us/intune/device-management/actions/#daily-tenant-limits).

### Delete action behavior by platform

When you use the **Delete** action in Intune, the command that triggers depends on the device platform and, for Android, the enrollment type.

- For **Apple mobile**, **macOS**, and **Windows** devices, the Delete action always triggers a **Retire** command.
- For **Android** devices, the Delete action triggers either a **Retire** or **Wipe** command depending on the enrollment type.

| Platform | Enrollment Type | Action Triggered |
| --- | --- | --- |
| Windows | Any | [Retire devices](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) |
| Apple mobile | Any | [Retire devices](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) |
| macOS | Any | [Retire devices](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) |
| Android | Device administrator | [Retire devices](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) |
| Android | Personally-owned work profile \(BYOD\) | [Retire devices](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) |
| Android | Corporate-owned Fully managed \(COBO\) | [Wipe devices](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) |
| Android | Corporate-owned Dedicated \(COSU\) | [Wipe devices](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) |
| Android | Corporate-owned Work profile \(COPE\) | [Wipe devices](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) |
| Android | Open Source Project \(AOSP\) | [Wipe devices](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) |

## Before retiring or deleting a Microsoft Entra joined device

If you delete or retire the Intune object for a Microsoft Entra joined device that is protected by BitLocker, Intune triggers a sync that removes key protectors. This action suspends BitLocker on the OS volume as a safeguard to prevent unrecoverable encryption scenarios when the Entra object is deleted.

Before retiring a Microsoft Entra joined device, make sure to back up any critical data that might be lost during the process, such as:

- BitLocker recovery key
- Local administrator account credentials

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Android
> - iOS/iPadOS
> - macOS
> - tvOS
> - visionOS
> - Windows

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Managed devices/Delete**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to delete a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Delete**. To confirm, select **Yes**.

Note

This action might be governed by an Intune access policy that requires Multiple Administrative Approval \(MAA\). If so, a second administrator must approve the action before it can proceed.

For more information, see [Use access policies to require multiple administrative approvals](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/multi-admin-approval).

## Remove a device from Microsoft Entra ID

After executing the action on a device from Intune, you might also want to remove its record from Microsoft Entra ID to fully disconnect it from your organization's identity infrastructure. This step helps ensure that the device no longer appears in your tenant, avoids potential confusion in device inventory, and prevents lingering access permissions or stale records that could affect compliance or reporting.

For more information about removing devices from Microsoft Entra ID, see [Manage stale devices in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/devices/manage-stale-devices).

## Remove an Apple ADE device from Apple Business Manager

After executing the action on an Apple Automated Device Enrollment \(ADE\) device in Intune, you might also need to release the device from Apple Business Manager to fully remove it from organizational control.

Follow these steps:

1. Go to [business.apple.com](http://business.apple.com), navigate to the **Devices** section, and search for the device using its serial number.
2. Select the device, opent the **...** menu, and the select **Release from Organization**.
3. Confirm the action by checking **I understand this cannot be undone**, and then select **Continue**.

Note

In some cases, the iOS device must be restored with iTunes to apply this change. Please find further instructions from Apple [here](https://support.apple.com/guide/itunes/restore-to-factory-settings-itnsdb1fe305/windows).

## Delete action status

After you issue a **Delete** action, the device is removed from Intune management and is immediately hidden from the admin center. In the [Device actions report](https://learn.microsoft.com/en-us/intune/device-management/reports/overview#device-actions-report), the Delete action is reported with an **Action Status** of **Completed**.

Note

For **MDM devices**, deleting a device immediately hides it from the admin center and initiates a **Retire**. A status of **Completed** on a delete action means the process is complete on the server side; it doesn't confirm that the client device finished the **Retire**.

## Reference links

- Microsoft Graph API: [delete action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-cleanwindowsdevice)
