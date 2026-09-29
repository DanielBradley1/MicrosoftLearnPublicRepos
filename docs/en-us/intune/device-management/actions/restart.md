<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/restart -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Device action: restart

The *restart* action triggers a restart \(usually begins within 5 minutes\) and might not show a warning to the signed-in user.

Important

The restart depends on the device receiving a push notification. If the device is offline or push notifications are blocked, the restart is delayed until connectivity resumes.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned Dedicated \(COSU\)
> - Android Enterprise corporate-owned Fully Managed \(COBO\)
> - Android Open Source Project \(AOSP\)
> - ChromeOS \(kiosk mode or managed guest session\)
> - iOS/iPadOS in [Supervised Mode](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-supervised-mode)
> - macOS
> - tvOS 10.2+ in [Supervised Mode](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-supervised-mode)
> - Windows

Note

Restart is only available for kiosk devices and managed guest session devices. The restart fails on any other type of device. For more information, see [Kiosk apps, managed guest sessions, and smart cards](https://support.google.com/chrome/a/topic/6128720?) \(opens Google Chrome Enterprise Help\).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Reboot now**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to restart a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Remote actions** > **Restart** > **Yes**.

## User experience

A passcode-locked device can't reconnect to Wi-Fi until the user unlocks it. Apple encrypts saved Wi-Fi credentials until unlock. Until then, Intune can't communicate with the device.

When the 5‑minute restart timer starts, Windows attempts to show the notification: *Your device administrator has scheduled a reboot.* Delivering the restart command requires Windows Notification Services \(WNS\).

For more information about WNS, see [Network endpoint requirements](https://learn.microsoft.com/en-us/intune/fundamentals/endpoints#windows-push-notification-services-wns-dependencies).

## Reference links

- Configuration service provider \(CSP\) used to initiate the action: [Reboot CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/reboot-csp)

- Microsoft Graph API: [rebootNow action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-rebootnow)
