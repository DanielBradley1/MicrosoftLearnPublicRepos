<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# Device action: Lost Mode

The *Lost Mode* device action in Microsoft Intune allows IT administrators to remotely lock and track lost or stolen devices. When activated, Lost Mode displays a custom message and contact phone number on the device's lock screen—helping facilitate recovery while protecting corporate data.

Once enabled, the device is locked and can't be accessed until Lost Mode is disabled by an administrator. While in Lost Mode, the device's location can also be tracked with the **[Locate device](https://learn.microsoft.com/en-us/intune/device-management/actions/locate)** action, making it easier to recover.

Chrome Enterprise and the Google Admin console refer to devices in lost mode as *disabled*. For more information about how to disable a device, see the Chrome Enterprise and Education Help documentation.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - iOS/iPadOS in [Supervised Mode](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/enable-supervised-mode)
> - ChromeOS

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, at a minimum, use an account that has one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permissions **Remote tasks/Enable lost mode**, **Remote tasks/Disable lost mode**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to enable Lost Mode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Lost mode \(supervised only\)**.
4. Under **Lost mode**, select **Enable**.
5. In the **Message to display on lock screen**, type a message to display on the device's lock screen.
6. Optionally, enter a phone number in the **Phone number to display** box.
7. Select **OK** to save your changes.

Tip

In the message you enter to show on the lock screen, include specific details to return the lost device.

## User experience

When you enable Lost Mode, the device is locked. The custom message and phone number you specify are displayed on the lock screen, helping facilitate recovery. While Lost Mode is active, the user can't access the device.

To locate the device during this time, use the [Locate device](https://learn.microsoft.com/en-us/intune/device-management/actions/locate) action in the admin center.

Note

Some built-in device functionalities might still work. For example, Siri might still be used to make calls unless it's disabled.

## How to disable Lost Mode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device, and then **Lost mode \(supervised only\)**.
3. Under **Lost mode**, select **Disable**.
4. Select **OK** to save your changes.

## Reference links

- Microsoft Graph API:

  - [enableLostMode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-enablelostmode)
  - [disableLostMode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-disablelostmode)
