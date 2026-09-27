<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/sync -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# Device action: sync

The *sync* device action forces a device to check in with Intune. When a device checks in, it receives any pending actions or policies assigned to it. This action is useful for validating and troubleshooting policy deployment without waiting for the next scheduled check-in.

For more information about the standard Intune policy check-in frequencies, see [Refresh cycle times](https://learn.microsoft.com/en-us/intune/device-configuration/troubleshoot-device-profiles#policy-refresh-intervals).

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
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Sync devices**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## Sync a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Sync**.
4. To confirm, select **Yes**.

## Sync behavior on Windows

After selecting **Sync**, Intune initiates an on-demand synchronization across multiple workloads to help ensure the device reflects the latest admin intent as quickly as possible. This process includes, but isn't limited to:

- Configuration policy processing
- App detection and deployment state updates
- Script and remediation processing
- Other device management signals required to align device state with current assignments

You can track the progress of the sync action by selecting the **Device sync status** tab in the device overview pane.

Note

The described sync behavior, including the **Device sync status** tab, applies only to Windows and iOS/iPadOS devices. To see the new device sync improvements, ensure that the 'Preview new device view' toggle is turned ON. This is at the top right of the Intune admin console screen.

## Sync behavior on iOS/iPadOS

After selecting **Sync**, Intune initiates an on-demand synchronization across multiple workloads to help ensure the device reflects the latest admin intent as quickly as possible. This process includes, but isn't limited to:

- Configuration policy processing
- App detection and deployment state updates
- Script and remediation processing
- Other device management signals required to align device state with current assignments

You can track the progress of the sync action by selecting the **Device sync status** tab in the device overview pane.

Note

The described sync behavior, including the **Device sync status** tab, applies only to iOS/iPadOS and Windows devices. To see the new device sync improvements, ensure that the 'Preview new device view' toggle is turned ON. This is at the top right of the Intune admin console screen.

## Retryable error codes

When you run the **Sync** action, apps that fail and raise a retryable error code remain available to the device. Apps that raise a nonretryable error code must wait seven days before they're available to the device.

| Error code | Suggested description | Retryable |
| --- | --- | --- |
| 2016330898 | An unknown error occurred. | No |
| 2016330897 | Your connection to Intune timed out. Reset your connection. | Yes |
| 2016330896 | You lost connection to the Internet. Reset your connection. | Yes |
| 2016330895 | You lost connection to the Internet. Reset your connection. | Yes |
| 2016330894 | You lost connection to the Internet. Reset your connection. | Yes |
| 2016330893 | You lost connection to the Internet. Reset your connection. | Yes |
| 2016330892 | International roaming is disabled. | No |
| 2016330891 | The cellular data connection for this device can't be accessed while a phone call is being made. Wait for the phone call to complete. | Yes |
| 2016330890 | The cellular network for this device. These devices couldn't be used at this time. | No |
| 2016330889 | The secure connection failed. Reset your connection. | Yes |
| 2016330888 | The server trust evaluation has failed. | No |

## Reference links

- Microsoft Graph API: [syncDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-syncdevice)
