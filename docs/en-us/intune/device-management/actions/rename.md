<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/rename -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Rename a device in Microsoft Intune

Renaming a device changes the **Device name** displayed in the Microsoft Intune admin center. It doesn't affect the *Management name* in Intune or the *Device name* shown in the Company Portal. Renaming helps you keep names consistent across your inventory—for example, aligning names with asset tags, user roles, or location-based identifiers.

You rename a single device from its **Properties** tab, or rename multiple devices at once by using **Bulk Device Actions**.

## Supported platforms

Rename is supported on:

- Android Enterprise corporate-owned Fully Managed \(COBO\), Dedicated \(COSU\), and Corporate-Owned Work Profile \(COPE\)
- iOS/iPadOS in [Supervised mode](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-supervised-mode)
- macOS \(corporate-owned\)
- Windows \(corporate-owned\)

Note

- **Android Enterprise**: Renaming changes only the **Device name** in the admin center, not the name on the device. This friendly name is one that users can change. It can take 10 minutes or more for a renamed device to update in the **Devices** list.
- **Windows**: Renaming Microsoft Entra hybrid joined devices from Intune isn't supported. To rename hybrid joined devices, use domain-based methods outside Intune.
- **iOS/iPadOS**: If you use an enrollment profile with a Device Name Template, the device is renamed but reverts to the template after the next sync with Intune.

## Rename a single device

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. Select the **Properties** tab, and then select **Edit**.
4. Update the device name. The allowed characters depend on the platform:

   - **Windows**: 63 characters or fewer \(excluding trailing NULL\); not null or empty; letters \(a–z, A–Z\), numbers \(0–9\), and hyphens; Unicode characters ≥ 0x80 must be valid UTF-8 and IDN-mappable; names can't be only numbers; no spaces; and these characters aren't allowed: `{ | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ( ) + / , . _ *`
   - **iOS/iPadOS and macOS**: Letters, numbers, and hyphens. The name must contain at least one letter or hyphen.
   - **Android**: Letters, numbers, and hyphens.

5. For Windows, to restart the device after renaming, set **Restart after rename** to **Yes**.
6. Save your changes.

## Bulk rename devices

You can rename devices in bulk by platform, using **Bulk Device Actions**. Bulk rename follows the same naming rules as a single rename, but you must include one of the following variables in the name:

- `{{serialnumber}}` — adds the device's serial number to the name.
- `{{rand:x}}` — adds a random string of numbers, where *x* is the number of digits.

To bulk rename devices:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. Select **Bulk Device Actions**.
3. On the **Basics** page, select the **OS** of the devices you want to rename, and for **Device action** select **Rename**.
4. Complete the configuration wizard.

## Reference links

- Microsoft Graph API: [setDeviceName action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-setdevicename)
- Configuration service provider \(CSP\) used to initiate the rename action on Windows: [Accounts CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/accounts-csp)

## Next steps

- [Edit other device properties](https://learn.microsoft.com/en-us/intune/device-management/actions/edit-device-properties) \(ownership, primary user, notes, and scope tags\).
- To change the device name shown in the Company Portal, see [Rename a device from the Company Portal](https://learn.microsoft.com/en-us/intune/user-help/device-actions/update-device-name-company-portal-app).
