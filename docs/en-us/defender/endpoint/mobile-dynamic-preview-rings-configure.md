<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mobile-dynamic-preview-rings-configure -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Configure Dynamic Preview Rings for Microsoft Defender on mobile

Organizations often need to validate new experiences and capabilities before they deploy them broadly. Traditionally, this validation requires distributing separate preview builds of the app and managing more enrollment or distribution processes.

Dynamic Preview Rings let you evaluate upcoming Microsoft Defender mobile experiences on Android and iOS devices without distributing separate preview builds of the app. Use a Microsoft Intune [app configuration policy](https://learn.microsoft.com/en-us/intune/app-management/configuration/overview) for managed devices or managed apps to enable preview features for a pilot group in the production version of the Microsoft Defender app. Users outside the pilot group continue to receive only generally available features. A yellow banner at the top of the Microsoft Defender app indicates that preview features are active, which matches the behavior in the nonproduction build.

Intune delivers the `DefenderPreview` setting from the app configuration policy to the Microsoft Defender app. A value of `1` enables Dynamic Preview. A value of `0`, or removing the key from the policy, returns the app to production features.

The benefits of Dynamic Preview Rings are:

- Eliminates the need to distribute nonproduction builds of the Microsoft Defender mobile app for preview testing.
- Removes the requirement to collect personal Gmail IDs for Android testing in non-MDM scenarios, which addresses privacy concerns.
- Accelerates testing by using your existing configuration policy workflows.

The limitations of Dynamic Preview Rings are:

- Currently, Dynamic Preview Rings don't support enabling or disabling individual preview features independently. Preview participation is assigned at the preview audience level.
- On Android, Dynamic Preview Rings don't work if you use [Microsoft Tunnel](https://learn.microsoft.com/en-us/intune/device-security/microsoft-tunnel/overview) features \(exclusively or with Microsoft Defender\).

Important

Dynamic Preview provides early access to preview features before they're generally available. Preview features are provided for evaluation purposes and might contain known or unknown issues, limitations, or incomplete functionality. As with other preview programs, preview features aren't intended for production use and might change before general availability.

Support and response processes for issues that occur only in preview features might differ from the processes for generally available features. Standard incident management \(ICM\) service-level agreement \(SLA\) commitments might not apply unless the issue is reproducible in a generally available \(production\) feature.

The set of preview features changes over time.

## Requirements

- Microsoft Defender for Endpoint must be deployed to your managed mobile devices.

  Intune is a separate product that isn't part of Microsoft Defender for Endpoint, and it isn't included in all subscriptions. You need a subscription that includes Intune, or you can buy Intune separately as a standalone subscription or add-on. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).
- An account assigned the Microsoft Intune [Application Manager role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#application-manager), or a custom Intune role with equivalent **Managed apps** and **Mobile apps** permissions.
- Identify the users or groups that participate in preview validation. No Microsoft Entra role is required to assign the policy to an existing group. To create the group or manage its membership, you need the appropriate Microsoft Entra permissions, such as the **Groups Administrator** role, or you must be an owner of the group.

### Supported platforms

- Android
- iOS/iPadOS

On both platforms, use a Microsoft Intune app configuration policy for managed devices or managed apps to deliver the `DefenderPreview` setting.

## Configure Dynamic Preview Rings on Android

You configure the `DefenderPreview` key for Android by using either a managed devices policy or a managed apps policy.

### Configure on Android using MDM

Note

Before you create the policy, add and approve **Defender: Antivirus** from Managed Google Play, and then sync it to Intune. After the sync, the app appears in Intune as **Microsoft Defender: Antivirus**. If no Android apps are synced from Managed Google Play, the target app list is empty and you see the message "You have not added any Android apps from the managed Google Play store." For deployment steps, see [Deploy Microsoft Defender for Endpoint on Android with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/deploy-android).

You can enable Dynamic Preview on enrolled Android devices using a **Managed devices** app configuration policy. For detailed instructions, see [Create an app configuration policy](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-android#create-an-app-configuration-policy) or [Update an app configuration policy](https://learn.microsoft.com/en-us/intune/app-management/configuration/overview) \(links open new tabs in the Intune documentation\).

When you create the policy, use these specific settings:

- **Policy type**: On the **Apps \| Configuration** page in the Microsoft Intune admin center at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Apps/ConfigPoliciesMenu/~/appConfigurationPolicies](https://intune.microsoft.com/#view/Microsoft_Intune_Apps/ConfigPoliciesMenu/%7E/appConfigurationPolicies), select **Create** > **Managed devices**.
- **Platform**: Select **Android Enterprise**.
- **Profile type**: Select one of the following values:

  - **All Profile Types**: Applies the policy to all supported enrollment types.
  - **Fully Managed, Dedicated, and Corporate-Owned Work Profile Only**: For corporate-owned, personally enabled \(COPE\) and corporate-owned, business only \(COBO\) devices.
  - **Personally-Owned Work Profile Only**: For bring-your-own-device \(BYOD\) devices.

- **Target app**: Select **Select app**, find and select **Microsoft Defender: Antivirus**, and then select **OK**.

When you create or modify the policy, use these specific settings in the **Configuration settings** section:

1. **Configuration settings format**: Select **Use configuration designer**, and then select **Add**.
2. In the flyout that opens, use the search box to find **Defender Preview**, select **\[Preview\] Defender Preview** from the results, and then select **OK**.
3. In the **\[Preview\] Defender Preview** entry, set **Configuration value** to `1` \(the default value is `0`\).

To confirm the policy is applied, verify that **DefenderPreview** is present and set to `1` on the target device.

### Configure on Android using MAM

You can enable Dynamic Preview on enrolled or unenrolled Android devices using a **Managed apps** app configuration policy. For detailed instructions, see [Add an app configuration policy for managed apps](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-apps#add-an-app-configuration-policy-for-managed-apps-on-iosipados-and-android-devices) or [Update an app configuration policy](https://learn.microsoft.com/en-us/intune/app-management/configuration/overview) \(links open new tabs in the Intune documentation\).

When you create the policy, use these specific settings:

- **Policy type**: On the **Apps \| Configuration** page in the Microsoft Intune admin center at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Apps/ConfigPoliciesMenu/~/appConfigurationPolicies](https://intune.microsoft.com/#view/Microsoft_Intune_Apps/ConfigPoliciesMenu/%7E/appConfigurationPolicies), select **Create** > **Managed apps**.
- **Target policy to**: Verify **Selected apps** is selected.
- **Public apps**: Select **Select public apps**, find and select **Microsoft Defender Endpoint Android**, and then select **Select**.

When you create or modify the policy, use these specific settings in the **General configuration settings** section:

- **Name**: Enter `DefenderPreview`.
- **Value**: Enter `1`.

## Configure Dynamic Preview Rings on iOS

You configure the `DefenderPreview` key for iOS by using either a managed devices policy or a managed apps policy.

### Configure on iOS using MDM

Note

Before you create the policy, add the Microsoft Defender app from the Apple App Store to Intune so it appears in the target app list. If no iOS store apps are added to Intune, the target app list is empty and you can't select the app. For deployment steps, see [Deploy Microsoft Defender for Endpoint on iOS with Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/ios-install).

You can enable Dynamic Preview on enrolled iOS devices using a **Managed devices** app configuration policy. For detailed instructions, see [Create an app configuration policy](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-ios#create-an-app-configuration-policy) or [Update an app configuration policy](https://learn.microsoft.com/en-us/intune/app-management/configuration/overview) \(links open new tabs in the Intune documentation\).

When you create the policy, use these specific settings:

- **Policy type**: On the **Apps \| Configuration** page in the Microsoft Intune admin center at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Apps/ConfigPoliciesMenu/~/appConfigurationPolicies](https://intune.microsoft.com/#view/Microsoft_Intune_Apps/ConfigPoliciesMenu/%7E/appConfigurationPolicies), select **Create** > **Managed devices**.
- **Platform**: Select **iOS/iPadOS**.
- **Target app**: Select **Select app**, find and select **Microsoft Defender: Security**, and then select **OK**.

When you create or modify the policy, use these specific settings:

- **Configuration settings format**: Select **Use configuration designer**.
- **Configuration key**: Enter `DefenderPreview`.
- **Value type**: Select **Integer**.
- **Configuration value**: Enter `1`.

To confirm the policy is applied, verify that **DefenderPreview** is present and set to `1` on the target device.

### Configure on iOS using MAM

You can enable Dynamic Preview on enrolled or unenrolled iOS devices using a **Managed apps** app configuration policy. For detailed instructions, see [Add an app configuration policy for managed apps](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-apps#add-an-app-configuration-policy-for-managed-apps-on-iosipados-and-android-devices) or [Update an app configuration policy](https://learn.microsoft.com/en-us/intune/app-management/configuration/overview) \(links open new tabs in the Intune documentation\).

When you create the policy, use these specific settings:

- **Policy type**: On the **Apps \| Configuration** page in the Microsoft Intune admin center at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Apps/ConfigPoliciesMenu/~/appConfigurationPolicies](https://intune.microsoft.com/#view/Microsoft_Intune_Apps/ConfigPoliciesMenu/%7E/appConfigurationPolicies), select **Create** > **Managed apps**.
- **Target policy to**: Verify **Selected apps** is selected.
- **Public apps**: Select **Select public apps**, find and select **Microsoft Defender Endpoint iOS/iPadOS**, and then select **Select**.

When you create or modify the policy, use these specific settings in the **General configuration settings** section:

- **Name**: Enter `DefenderPreview`.
- **Value**: Enter `1`.

## Related content

- [Resources for Microsoft Defender for Endpoint for mobile devices](https://learn.microsoft.com/en-us/defender-endpoint/mobile-resources-defender-endpoint)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
