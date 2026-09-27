<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/rename -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: rename

The *rename device* action in Microsoft Intune allows IT administrators to change the *Device name* displayed in the Intune admin center for a managed device. This action does not affect the *Management name* in Intune or the *Device name* shown in the Company Portal.

Renaming a device can help improve clarity and consistency across your device inventory—especially in environments with shared devices, standardized naming conventions, or large-scale deployments. It's useful for aligning device names with asset tags, user roles, or location-based identifiers, making it easier to manage and troubleshoot devices at scale.

Note

Renaming Android Enterprise devices only changes the **Device name** in the Intune admin center and not on the device itself. The Device name in Intune is a friendly name that users can change.

Note

Renaming Microsoft Entra hybrid joined devices from Intune is not supported. To rename hybrid joined devices, use domain-based methods outside of Intune.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned Fully Managed \(COBO\)
> - Android Enterprise corporate-owned Dedicated \(COSU\)
> - Android Enterprise corporate-owned Work Profile \(COPE\)
> - iOS/iPadOS in [Supervised Mode](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-supervised-mode)
> - macOS \(corporate-owned\)
> - Windows \(corporate-owned\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Set device name**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to rename a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Rename device**.

4. In the **Rename device** pane, type the new name in the text box. The new name must follow these rules:

   - Less than or equal to 63 characters, not including trailing NULL
   - Not null or an empty string
   - Allowed ASCII: Letters \(a-z, A-Z\), numbers \(0-9\), and hyphens
   - Allowed Unicode: characters >= 0x80, must be valid UTF8, must be IDN-mappable \(that is, RtlIdnToNameprepUnicode succeeds; see RFC 3492\)
   - Names must not contain only numbers
   - No spaces in the name
   - Disallowed characters: ```{ | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % `` ( ) + / , . _ *)```

4. In the **Rename device** pane, type the new name in the text box. You can use letters, numbers, and hyphens. The name must contain at least one letter or hyphen.

4. In the **Rename device** pane, type the new name in the text box. You can use letters, numbers, and hyphens.

5. If you want to restart the device after renaming it, Select **Yes** next to **Restart after rename**.
6. Select **Rename**.

Note

If you have an iOS enrollment profile with a Device Name Template, the device will be renamed but will revert to the template after the next sync with Intune.

Note

It could take 10 minutes or more for a renamed Android Enterprise device to update in the **Devices** list.

## How to bulk rename devices from the Intune admin center

You can choose to rename devices in bulk, based on the device platform. The bulk rename option uses the same rules as renaming a single device. However, you must also include one of the following variables as part of the device name:

- `{{serialnumber}}` - Add the device's serial number to the name.
- `{{rand:x}}` - Add a random string of numbers, where x equals the number of digits to add.

To use the bulk rename action:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. Select **Bulk Device Actions**.
3. On the Basics page, for **OS** select the platform of the devices you want to rename, and then for **Device action** select **Rename**.
4. Complete the configuration wizard.

## Reference links

- Microsoft Graph API: [setDeviceName action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-setdevicename)

- Configuration service provider \(CSP\) used to initiate the action: [Accounts CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/accounts-csp)

## Next steps

To learn how to change the Device name shown in the Company Portal, see [Rename device from the Company Portal](https://learn.microsoft.com/en-us/intune/user-help/device-actions/update-device-name-company-portal-app).
