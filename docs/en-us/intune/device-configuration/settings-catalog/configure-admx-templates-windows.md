<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-admx-templates-windows -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Configure ADMX settings using the settings catalog in Microsoft Intune

The [Intune settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/) includes **Administrative Templates** that you can use to help manage Windows client devices. These settings are built in to Intune \(no downloading\), and don't require any customizations, including using OMA-URI.

This feature applies to:

- Windows

You can import custom and non-Microsoft ADMX and ADML files. For more information, see [Import custom or partner ADMX files](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/import-custom-admx-templates).

This article describes the steps to use the administrative templates in the settings catalog. When the settings catalog policy is created, you can assign or deploy this profile to Windows client devices in your organization.

## Before you begin

- Some settings aren't included in all Windows editions. For the best experience, we recommend using the Windows Enterprise edition.
- The Windows settings use the [Windows policy CSPs](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies). The CSPs work on different editions of Windows, such as Home, Professional, Enterprise, and so on. To see if a CSP works on a specific edition, go to [Windows policy CSPs](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies).
- The Windows settings in Intune correlate to the on-premises group policy path you see in Local Group Policy Editor \(`gpedit`\).
- Starting with the December 2412 release, the **Templates** > **Administrative Templates** profile type in the Intune admin center is deprecated and read-only. For more information on this change, see [Windows device configuration policies migrating to unified settings platform in Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/support-tip-windows-device-configuration-policies-migrating-to/ba-p/4189665).

  If you use custom ADMX templates, you can still [import administrative templates](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/import-custom-admx-templates).

## Create the policy

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following properties:

   - **Platform**: Select **Windows 10 and later**.
   - **Profile type**: Select **Settings catalog**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

   - **Name**: Name your profiles so you can easily identify them later. For example, a good profile name is **ADMX: Configures screen saver**.
   - **Description**: This setting is optional but recommended.

6. Select **Next**.
7. Select **Add settings**, and expand **Administrative Templates**. Select any setting to see what you can configure.

   [![Screenshot that shows how to expand administrative templates in a settings catalog policy in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/media/configure-admx-templates-windows/settings-catalog-administrative-templates.png)](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/media/configure-admx-templates-windows/settings-catalog-administrative-templates.png#lightbox)
8. When you select a setting, you can see `(User)` in the setting name. `(User)` means that the settings apply to users when they sign in. Settings that don't have `(User)` in the setting name apply to devices.

   [![See the settings that apply to users and that apply to devices in the settings catalog in Microsoft Intune and Intune admin center](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/media/configure-admx-templates-windows/settings-catalog-administrative-templates-user.png)](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/media/configure-admx-templates-windows/settings-catalog-administrative-templates-user.png#lightbox)
9. Select a setting you want to configure. For example, expand **Control Panel** > **Personalization** > select **Enable screen saver \(User\)**. Close the settings picker.

   When you select the setting, it's added to the policy, and ready for you to configure:

   [![See a sample setting in the settings catalog in Microsoft Intune and Intune admin center that you can configure](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/media/configure-admx-templates-windows/settings-catalog-administrative-templates-sample-setting.png)](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/media/configure-admx-templates-windows/settings-catalog-administrative-templates-sample-setting.png#lightbox)
10. Select **Next**.
11. In **Scope tags** \(optional\), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information, see [Use role-based access control \(RBAC\) and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
12. In **Assignments**, select the user or groups that receive your profile. For more information, see [Assign user and device profiles in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).

    If the profile is assigned to user groups, the configured settings apply to any device that the user enrolls and signs in to. If the profile is assigned to device groups, the configured settings apply to any user that signs in to that device. This assignment happens if the setting is a computer configuration \(`HKEY_LOCAL_MACHINE`\) or a user configuration \(`HKEY_CURRENT_USER`\). With some settings, a computer setting assigned to a user can also affect the experience of other users on that device.

    For more information, see [User groups vs. device groups when assigning policies](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile#user-groups-vs-device-groups).

    Select **Next**.
13. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned to the groups you selected. The policy is also shown in the profiles list.

The next time the device checks for configuration updates, the settings you configured are applied.

## Create a Known Issue Rollback policy

On your enrolled devices, you can use administrative templates to create a Known Issue Rollback \(KIR\) policy and deploy this policy to your Windows devices. See [Deploy a KIR activation using Microsoft Intune ADMX policy ingestion to managed devices](https://learn.microsoft.com/en-us/troubleshoot/windows-client/group-policy/use-group-policy-to-deploy-known-issue-rollback#deploy-a-kir-activation-using-microsoft-intune-admx-policy-ingestion-to-the-managed-devices).

For more information about KIR, see:

- [Known Issue Rollback: Helping you keep Windows devices protected and productive](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/known-issue-rollback-helping-you-keep-windows-devices-protected/ba-p/2176831)
- [How to use on-premises Group Policy or Intune to deploy a Known Issue Rollback](https://learn.microsoft.com/en-us/troubleshoot/windows-client/group-policy/use-group-policy-to-deploy-known-issue-rollback)

## Related content

- [assign the template \(also called a profile\)](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor the policy status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- [Update Office using the settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/update-office).
- [Restrict USB devices using the settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/restrict-usb).
- [Create Microsoft Edge policy using the settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-edge).
- [Import custom or partner ADMX files](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/import-custom-admx-templates).
