<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/disable-activation-lock -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# Device action: disable Activation Lock

Activation Lock is a security feature built into the *Find My* app on iOS/iPadOS and macOS devices. When enabled, it prevents unauthorized access by requiring the user's Apple ID and password to:

- Turn off Find My
- Erase the device
- Reactivate the device

Activation Lock is automatically enabled when a user sets up Find My on a device.

## Activation Lock impact for organizations

While Activation Lock helps protect devices from theft or loss, it can create challenges for IT admins managing device lifecycles. For example:

- A user enables Activation Lock, then leaves the organization. Without their Apple ID credentials, the device can't be reactivated.
- You need to reassign devices during a refresh or transfer, but Activation Lock prevents reuse.

These scenarios can delay provisioning, increase support overhead, and impact operational efficiency.

To help solve these problems, Apple introduced the ability to disable Activation Lock for supervised devices, without the user's Apple ID and password. Supervised devices generate a device-specific Activation Lock bypass code, which is stored on Apple's activation server.

To dive deeper into how Activation Lock works, see [Activation Lock for iPhone and iPad](https://support.apple.com/HT201365).

## How Intune helps you manage Activation Lock

There are two methods to disabling Activation Lock on devices:

- Manually entering the Activation Lock bypass code on the device.
- Using the *disable Activation* Lock device action.

For supervised devices, Intune stores the Activation Lock bypass code, which can be entered on the device to manually disable Activation Lock. If the device has been wiped, you can directly access the device by using a blank username and the code as the password. Additionally, Intune can directly issue the bypass code to Apple's activation server to disable Activation Lock without having to interact with the device.

The business benefits of using Intune to manage Activation Lock are:

- The user gets the security benefits of the Find My app.
- You can enable users to do their work and unlock it when a device needs to be repurposed, without needing the previous username or password.

Tip

You can also turn off Activation Lock directly in Apple Business Manager and Apple School Manager. To learn more, see [Turn off Activation Lock in Apple Business Manager](https://support.apple.com/guide/apple-business-manager/axm812df1dd8).

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - iOS/iPadOS in [Supervised Mode](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-supervised-mode) through Automated Device Enrollment \(ADE\)
> - macOS [enrolled via Automated Device Enrollment \(ADE\)](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-macos)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> Before you can manage Activation Lock, you must configure your devices to allow it.
> 
> 1. [Create a Settings catalog policy](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/) for the iOS/iPadOS platform and use the following setting:
>    | Category | Setting name | Value |
>    | --- | --- | --- |
>    | **Managed Setting** > **MDM Options** | Activation Lock Allowed While Supervised | Allowed |
> 2. Assign the policy to a group that contains as members the devices that you want to configure.

> Before you can manage Activation Lock, you must configure your devices to allow it.
> 
> 1. [Create a Settings catalog policy](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/) for the macOS platform and use the following setting:
>    | Category | Setting name | Value |
>    | --- | --- | --- |
>    | **Managed Setting** > **MDM Options** | Activation Lock Allowed While Supervised | Allowed |
> 2. Assign the policy to a group that contains as members the devices that you want to configure.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - Intune Service Administrator
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Bypass activation lock**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to disable Activation Lock from the Intune admin center

The Disable Activation Lock device action in Intune removes Activation Lock without requiring the user's Apple ID and password. However, if the Find My app is launched after this action, Activation Lock will be automatically re-enabled. To avoid re-locking the device, make sure you have physical possession of the device before disabling Activation Lock.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Disable Activation Lock**.
4. Select **Hardware**, then find and copy the **Activation Lock bypass code** value under **Conditional Access**.

   Important

   If you reset the device settings before you copy the code, the code is removed from Intune and is inaccessible. **Ensure to copy the bypass code before you wipe the device.**

To retrieve the `activationLockBypassCode` property using Microsoft Graph, you must explicitly include it in your query. If you send an unfiltered request for the device object, Graph returns a default set of properties—and `activationLockBypassCode` will be `null`.

## How to use the Activation Lock bypass code from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Wipe**.

3. After the device is reset, you're prompted for the Apple ID and password. Leave the ID field blank, and then enter the **Activation Lock bypass code** for the password. This step removes the account from the device.

3. After the device is reset, select **Recovery Assistant** in the menu bar and then select **Activate with MDM key** option to enter the bypass code.

## Reference links

- Microsoft Graph API: [bypassActivationLock action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-bypassactivationlock)
