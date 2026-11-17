<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-shared-device -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Control access, accounts, and power features on shared PC or multi-user Windows devices using Intune

Devices that have multiple users are called *shared devices*, and are a common part of mobile device management \(MDM\) solutions. Using Microsoft Intune, you can create and configure shared devices.

For example, schools have devices that many students typically use. School Intune admins can turn on the Shared PC feature to allow one user at a time. Students can't switch between different signed-in accounts on the device. When the student signs out, you can also choose to remove all user-specific settings.

With this feature:

- End users can sign in to these shared devices with a guest account. After users sign in, the credentials are cached.
- You control if the guest account deletes when the user signs off, or delete inactive accounts when a threshold is reached.
- When end users use the device, they only get access to features you allow. For example, you:

  - Choose when the device goes into sleep mode
  - Decide if users can see and save files locally
  - Enable or disable power management settings

End users can sign in to these shared devices with a guest account. After users sign in, the credentials are cached. As they use the device, end users only get access to features you allow.

For example, you choose when the device goes into sleep mode, if users can see and save files locally, enable or disable power management settings, and more. You also control if the guest account deletes when the user signs off, or delete inactive accounts when a threshold is reached.

This article shows you how to create a shared multiple user device configuration profile, and includes links to the available settings.

When you create the profile in Intune, you deploy or assign the profile to device groups in your organization. You can also assign this profile to device groups with mixed device types and operating system \(OS\) versions.

This feature applies to:

- Windows Professional
- Windows Enterprise
- Windows Holographic for Business, such as the HoloLens

Tip

For iOS/iPadOS shared devices, see [shared device solutions for iOS/iPadOS](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/shared-device-solutions-ios).

## Prerequisites

- To create the policy, at a minimum, sign in with an account that has the **Policy and Profile Manager** Intune role. For more information, see [Role-based access control \(RBAC\) with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following properties:

   - **Platform**: Select **Windows 10 and later**.
   - **Profile type**: Select **Templates** > **Shared multi-user device**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the new profile.
   - **Description**: Enter a description for the profile. We recommend this optional setting.

6. Select **Next**.
7. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. Choose your platform for detailed settings:

   - [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-shared-device-settings-windows)
   - [Windows Holographic for Business](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-shared-device-settings-windows-holographic)

8. Select **Next**.
9. In **Scope tags** \(optional\), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use role based access control \(RBAC\) and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

   Select **Next**.
10. In **Assignments**, select the devices group that receives your profile. For more information, see [Assign user and device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).

    Select **Next**.

    Note

    Be sure to assign the profile to device groups in your organization.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time each device checks in, the policy is applied.

## Related content

- [Settings for Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-shared-device-settings-windows)
- [Settings for Windows Holographic for Business](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-shared-device-settings-windows-holographic)
- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile)
- [Monitor profile status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile)
