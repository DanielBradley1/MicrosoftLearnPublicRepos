<!-- Source: https://learn.microsoft.com/en-us/intune/app-management/collect-bundle-ids -->
<!-- Sitemap-Last-Modified: 2026-06-22 -->

# Get the App Bundle ID for Your Policies in Microsoft Intune

When you add an app to Intune or use the built-in apps, the bundle ID of the app is also added. This bundle ID identifies the app, and you can use the bundle ID in your policies.

For example, you can use the bundle ID in an Intune device configuration profile to allow or block specific apps.

Applies to:

- Android
- iOS/iPadOS
- macOS
- Windows

This article lists the steps to get the app bundle IDs using the Intune admin center.

## Get the app bundle ID

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **All Apps**.
3. Select **Columns**.

   ![Screenshot that shows how to select the Columns option in All Apps in Microsoft Intune and the Intune admin center.](https://learn.microsoft.com/en-us/intune/app-management/media/collect-bundle-ids/all-apps-column.png)
4. In the list, select **App identifier** > **Apply**.

   ![Screenshot that shows how to select the App Bundle ID column in All Apps in Microsoft Intune and the Intune admin center.](https://learn.microsoft.com/en-us/intune/app-management/media/collect-bundle-ids/columns-select-app-identifier.png)
5. The **App identifier** column shows the bundle ID of the app.

## Related articles

- [Add apps to Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/)
- [Bundle IDs for built-in iOS and iPadOS apps you can use in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-bundle-ids-ios)
- [Add built-in apps to Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-built-in)
