<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wired-networks -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# Add and use wired networks settings on your devices in Microsoft Intune

Organizations use wired networks to give network access to desktop computers and devices that must use a network cable.

Microsoft Intune includes built-in settings to configure wired networks for your iOS/iPadOS, macOS, and Windows devices. You can configure the network interface, accepted EAP types, enter server trust settings, and more.

These built-in settings can be deployed to devices in your organization using policy. When the policy is ready, it can be assigned to different users and groups. Once assigned, your users get access to your organization's wired network without configuring it themselves.

As part of your mobile device management \(MDM\) solution, use this feature to create 802.1x profiles to manage wired networks. Then, deploy these wired networks to your devices.

## Example scenario

You have a wired network named **Contoso wired network**. You want to set up all macOS desktops to connect to this network. Here's the process:

1. In Intune, create a wired network profile that includes the settings that connect to the **Contoso wired network**.
2. Assign the profile to a group that includes all users macOS desktop computers. For recommendations on using group types, go to [User groups vs. device groups](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile#user-groups-vs-device-groups).
3. On their desktops, users find the **Contoso wired network** in the list of networks. They can then connect to the network, using the authentication method of your choosing.

This article lists the steps to create a wired network profile in Intune. It also includes links that describe the different settings.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This feature supports the following platforms:
> 
> - iOS/iPadOS
> - macOS
> - Windows

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following properties:

   - **Platform**: Select **iOS/iPadOS**, **macOS**, or **Windows 10 and later**.
   - **Profile type**: Select **Templates** > **Wired network**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **macOS-Wired network policy**.
   - **Description**: Enter a description for the profile. This setting is optional, but recommended.

6. Select **Next**.
7. In **Configuration settings**, configure the settings, including the Extensible Authentication Protocol \(EAP\) type. For a list of all settings, and what they do, go to:

   - [Apple](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wired-network-settings-macos)
   - [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wired-network-settings-windows)

8. Select **Next**.
9. In **Assignments**, select the user groups or device groups that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).

   Select **Next**.
10. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

Tip

If you use certificate based authentication for your wired network profile, then deploy the wired network profile, certificate profile, and trusted root profile to the same groups. This deployment makes sure that each device can recognize the legitimacy of your certificate authority. For more information, go to [configure certificates with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview).

## Related articles

The profile is created, but might not be doing anything. Be sure to [assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
