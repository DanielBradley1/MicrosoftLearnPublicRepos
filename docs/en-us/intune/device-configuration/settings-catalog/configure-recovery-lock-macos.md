<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-recovery-lock-macos -->
<!-- Sitemap-Last-Modified: 2026-06-01 -->

# Configure Recovery Lock on macOS devices in Microsoft Intune

Recovery Lock helps protect your macOS devices against unauthorized reinstallation and wiping. When you add a Recovery Lock policy, Intune automatically generates a strong, random password and sets it on the device.

When you configure this feature:

- Users must enter the password to access the recovery partition environment on the device.
- The password is required to update or remove an existing password.
- The password can be reset automatically using a time-based rotation interval.
- Access to the **Startup Options** screen is protected.

Use the Intune [settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/) to configure Recovery Lock on your macOS devices. After you configure the policy, assign it to your macOS devices.

After you configure and assign the policy, you can use device actions to rotate the Recovery Lock passcode.

To learn more about the recoveryOS password and startup security, see [Startup security in macOS](https://support.apple.com/guide/deployment/startup-security-dep5810e849c/1/web/1.0) \(opens Apple's website\).

This article applies to:

- macOS

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This feature supports the following platforms:
> 
> - **macOS 11.5 or later** and use Apple silicon
> - Devices must be enrolled in Intune and supervised.
> 
> Recovery Lock isn't available for macOS devices with Intel chips.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To configure this policy in the settings catalog, use an account with at least one of the following roles:
> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).
> 
> To run the device actions, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account with one of the following roles:
> 
> - [Intune administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) Microsoft Entra role
> - An Intune [custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) with the following permissions:
> 
>   - Remote tasks/Rotate macOS recovery lock password
>   - Remote tasks/View macOS recovery lock password

## Create the Recovery Lock policy

Use the following steps to create a Recovery Lock policy in the settings catalog.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following properties:

   - **Platform**: Select **macOS**.
   - **Profile type**: Select **Settings catalog**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Enable recovery lock**.
   - **Description**: Enter a description for the profile. This setting is optional, but recommended.

6. Select **Next**.
7. In **Configuration settings**, select **Add settings**, and search for **Recovery Lock**. Select the **Recovery Lock Password** category, select **Select all these settings**, and then close the settings picker.

   [![Screenshot that shows Recovery Lock settings in the settings catalog in Microsoft Intune and Intune admin center.](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/media/configure-recovery-lock-macos/recovery-lock-category-settings.png)](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/media/configure-recovery-lock-macos/recovery-lock-category-settings.png#lightbox)
8. Configure the Recovery Lock settings:

   - **Enable Recovery Lock Password**: Select **Enabled** to enable the Recovery Lock feature on the device.
   - **Recovery Lock Password Rotation Schedule**: Enter the number of months before the Recovery Lock password is automatically reset, from 1 to 12 months.

     When the schedule triggers, Intune updates the password on the device and securely stores it in the Intune admin center.

     Be sure to set a schedule that meets your organization's security requirements. A shorter rotation interval increases security, as it reduces risk if a password is leaked. It can also increase help desk calls if users need to access the recovery partition often.

9. Select **Next**. In **Scope tags**, select **Next**.

   Scope tags are optional, and this example doesn't use them. To learn more about scope tags, and what they do, go to [Use role-based access control \(RBAC\) and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).
10. In **Assignments**, select **Next**.

    Assignments are optional, and this example doesn't use them. In production, select **Add groups**. Select a Microsoft Entra group that includes users or devices that should receive this policy. For information and guidance on assigning policies, see [Assign user and device profiles in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).
11. In **Review + create**, review the summary of your changes. Select **Create**.

    When you create the profile, your policy is automatically assigned to the users or groups you chose. If you didn't choose any users or groups, then your policy is created, but it isn't deployed.

    In **Devices** > **Configuration**, your new policy is shown in the list.

## Monitor Recovery Lock status and view the password

When you assign the policy to devices, you can monitor its status using the [Per setting status report](https://learn.microsoft.com/en-us/intune/device-management/reports/overview#per-setting-status-report-operational).

If Recovery Lock is enabled, you can view the password in the report at **Passwords and keys** > **Recovery Lock Password**.

## Use the rotate Recovery Lock passcode device action

You can use the rotate Recovery Lock passcode device action to reset the Recovery Lock password on demand. This action is helpful if a user forgets their password, or if you want to proactively rotate the password outside of the rotation schedule you set in the policy.

1. In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > **All devices** > select the macOS device.
2. Select **Secure** > **Rotate Recovery Lock Passcode**.
3. Select **Yes** to confirm the action. Intune generates a new Recovery Lock passcode.

To learn more, see [Rotate Recovery Lock passcode device action](https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-recovery-lock-passcode).

## Remove the Recovery Lock password

To remove the Recovery Lock password from a device, you have the following options:

- **Option 1**: When you unenroll the device from Intune, the Recovery Lock password is automatically cleared from the device.
- **Option 2**: When you unassign a device from the policy, Intune attempts to clear the Recovery Lock password.

## Related content

- [Use the Intune settings catalog to configure settings](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/)
- [Common tasks you can complete using the settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/common-tasks)
