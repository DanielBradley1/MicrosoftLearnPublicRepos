<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/locate -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# Device action: locate device

The *locate device* device action in Microsoft Intune enables IT administrators to pinpoint the physical location of managed devices when they are lost, stolen, or simply misplaced. This feature is especially valuable in organizations where devices are distributed across multiple sites or used by mobile users. By triggering the Locate device action from the Intune admin center, admins can view the device's location on a map, helping accelerate recovery, reduce downtime, and improve compliance.

Depending on the platform, Intune can also report the last known location if the device is offline, [play a sound to locate lost devices](https://learn.microsoft.com/en-us/intune/device-management/actions/play-lost-mode-sound), or [enable lost mode to display custom messages on devices](https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode).

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated \(COSU\)
> - Android Enterprise corporate-owned fully managed \(COBO\)
> - Android Enterprise corporate-owned work profile \(COPE\)
> - iOS/iPadOS in [Supervised Mode](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/enable-supervised-mode)
> - Windows

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> To use this action, make sure devices meet the following requirements:
> 
> - Enable [Lost Mode](https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode)

> To use this action, make sure devices meet the following requirements:
> 
> - Location services must be turned on.
> - Intune app is installed.
> 
> **Fully Managed Devices**:
> 
> - The **Locate Device** feature must be explicitly enabled with a device restrictions profile.
> 
> **Corporate-Owned Work Profile Devices**:
> 
> - The **Locate Device** feature must be explicitly enabled with a device restrictions profile.
> - Users must grant location permission to the Intune app. Go to: **Settings** > **Apps** > **Intune \(Work tab\)** > **Permissions** > **Location** > **Allow all the time**.
> 
> **Dedicated Devices**:
> 
> - The **Locate Device** feature is enabled by default, unless explicitly blocked with a device restriction profile.

Note

When **Locate device** is allowed, users receive a one-time notification, *Intune can access your location*, indicating that Intune has the ability to use location permissions on the device.

For more information about device restrictions, see [Android template device settings list to restrict features using Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android-enterprise).

> Before you can use the locate functionality, you must configure your devices to allow it.
> 
> 1. [Create a Settings catalog policy](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/) for the Windows platform and use the following setting:
>    | Category | Setting name | Value |
>    | --- | --- | --- |
>    | **Privacy** | Let Apps Access Location | Force allow |
> 2. Assign the policy to a group that contains as members the devices that you want to configure.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permissions **Remote tasks/Locate device**, **Remote tasks/Play sound to locate lost devices**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)
> 
> For Android devices, the action is available only if the admin can read the policies that configure device location.
> 
> The account must:
> 
> - Have the **Device configuration/Read** permission.
> - Have scope tag visibility to the device restriction or settings catalog policy that enables location for the device.

## Locate a device

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.

1. At the top of the device overview pane, find the row of action icons. Select **Locate device**.

1. At the top of the device overview pane, find the row of action icons. Select **Locate** > **Locate device**.

1. After the device is located, its location is shown in **Locate device**. You can select the location pin on the map to view a location address and coordinates.

Note

Android Enterprise corporate-owned dedicated \(COSU\) that aren't currently online can display their [last known location](#last-known-location) when the device last checked in within seven days.

![Map view showing the located device position with address and coordinates in the Intune admin center](https://learn.microsoft.com/en-us/intune/device-management/actions/media/locate/locate-device.png)

### Last known location

When you use the *Locate device* action for an Android Enterprise dedicated device that is offline and unable to respond with its current location, Intune attempts to display its last known location. This capability uses data submitted by the device when it checks in with Intune.

Intune collects information about the last known location of a device every eight hours or when the device checks in with Intune. Intune keeps this information for up to seven days. The last known location of a device that hasn't checked in with Intune for more than seven days can't be displayed.

**About initialization of last known location**:

To support the *last know location* capability for Android dedicated devices, each device receives an initial default entry for **Locate device** which shows a status of **Complete**. This status appears under *Device actions status* when you view the devices Overview page. This default status is a result of Intune initializing the capability by default, which doesn't mean a locate device action has run.

The date and time of this default status varies:

- Devices that are enrolled before the capability becomes available, reflect the day this capability was enabled for your tenant.
- Devices that you enroll after this capability is available, reflect the time of device enrollment.

Later, this default status updates to reflect the actual date and time that an admin runs the Locate device action for that device.

## Security and privacy information

Intune is designed to respect user privacy while providing powerful device management capabilities. When using the Locate Device action, here's what you need to know about how location data is handled:

- Location data is only collected when you initiate the Locate Device action—never before.
- Once triggered, the device's latitude and longitude are retrieved via the Graph API.
- All location data is encrypted in transit and at rest, ensuring secure handling.
- Data is stored for 24 hours and automatically deleted. Manual deletion is not supported.
- The last known location might be retained for up to seven days before being removed.
- On iOS/iPadOS devices, you can enable [Lost Mode](https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode) to remotely lock the device and display a custom message on the lock screen—helpful for recovery.
- In Android fully managed and corporate-owned work profile scenarios, users receive a notification when the Locate Device action is used—if notifications are enabled on the device.

## Reference links

- Microsoft Graph API:

  - [locateDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-locatedevice)
  - [playLostModeSound action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-playlostmodesound)
