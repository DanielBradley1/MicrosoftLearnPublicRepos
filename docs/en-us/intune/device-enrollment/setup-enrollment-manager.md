<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/setup-enrollment-manager -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Add device enrollment managers

A device enrollment manager \(DEM\) is a nonadministrator user who can enroll devices in Intune. Device enrollment managers are useful when you need to enroll and prepare many devices for distribution. People signed in to a DEM account can enroll and manage up to 1,000 devices, while a standard nonadmin account can only enroll 15.

Tip

The following enrollment methods allow standard nonadmin accounts to enroll more than 15 devices:

- Co-management with Configuration Manager
- Automatic enrollment + group policy
- Windows Autopilot

If you're using these methods to enroll devices, you don't need to use a DEM account.

A DEM account requires an Intune user or device license, and an associated Microsoft Entra user. This article describes the limits and specifications of DEM accounts and how to manage permissions.

## Supported enrollment methods

A device enrollment manager can use the following methods to enroll devices in Intune:

- [Bulk enrollment using a provisioning package](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/create-bulk-package)
- DEM-initiated via Company Portal enrollment
- DEM-initiated via Microsoft Entra join

Tip

To compare DEM best practices and capabilities alongside other Windows enrollment methods, see [Intune enrollment method capabilities for Windows devices](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/guide).

## Requirements

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To manage device enrollment manager accounts, you must be assigned the [**Intune Administrator**](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) role.

Important

On October 14, 2025, [Windows 10 reached end of support](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

### Permissions

The Intune Administrator role can *update* and *read* device enrollment manager accounts.

| Permission | Description |
| :--- | :--- |
| Update | Create new device enrollment manager accounts, or delete device enrollment manager accounts. |
| Read | View the list of device enrollment manager accounts. |

## Add a device enrollment manager

Tip

Only use dedicated accounts that aren't assigned to an individual user as Device enrollment manager accounts.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** > **Enrollment**.
3. Select the **Device enrollment managers** tab.
4. Choose **Add**.
5. In the **User name** field, enter the user principal name of the user you're adding.
6. Select **Add**. The new device enrollment manager is added to the list of DEM users.

To remove someone as a device enrollment manager, select their name in the list and then choose **Delete**.

Tip

Don't delete accounts assigned as a Device enrollment manager if any devices were enrolled by using the account. Doing so leads to issues with these devices.

## Limitations

You can't use the device enrollment manager account with all features in Microsoft Intune. It also has some limitations when used with other features. This section describes the limitations you might encounter while setting up devices from a DEM account.

### Android Enterprise

You can enroll up to 10 personally owned devices with work profiles.

You can't set up the following types of Android Enterprise devices by using DEM:

- Corporate-owned devices with a work profile
- Fully managed devices

### Android open source project \(AOSP\)

AOSP doesn't support DEM accounts.

### App assignments

No users are associated with a DEM-enrolled device, so you can't deploy apps as **Available**.

### Apple Automated Device Enrollment

DEM isn't compatible with Apple Automated Device Enrollment \(ADE\).

### Apple volume purchased apps

DEM-enrolled devices can install VPP apps if they have Apple VPP device licenses. You can't use apps purchased through Apple VPP with Apple VPP user licenses, because of per-user Apple ID requirements for app management.

### Certificates

You must use device-level certificates to manage Wi-Fi and email connections.

### Conditional Access

Conditional Access is only supported with DEM on devices that run:

- Windows 10, version 1803 and later
- Windows 11

Note

DEM accounts on iOS/iPadOS and macOS don't support Microsoft Entra Join, Microsoft Entra registration, and Workplace Join.

### Device limit restrictions

DEM enrolls Windows devices in shared device mode, so device limit restrictions don't work on them. Instead, configure a hard limit for these devices in the Microsoft Entra admin center. For more information, see [Manage device identities](https://learn.microsoft.com/en-us/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).

### Intune Company Portal

Only the local device appears in the Company Portal app or Company Portal website. Device users can't wipe DEM-enrolled devices from Company Portal. You need to sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) to wipe these devices.

### Microsoft Entra ID

If you apply a Microsoft Entra maximum device limit of less than 1,000 to a DEM account, you prevent the account from reaching the 1,000 device limit that the DEM account can enroll.

### Number of accounts

There's a limit of 150 DEM accounts in Microsoft Intune.

### VPN profiles

User-based VPN profiles don't work with DEM-enrolled devices.

## Related content

- [Set up enrollment notifications](https://learn.microsoft.com/en-us/intune/device-enrollment/setup-notifications)
- [Enrollment time grouping in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/setup-time-grouping)
