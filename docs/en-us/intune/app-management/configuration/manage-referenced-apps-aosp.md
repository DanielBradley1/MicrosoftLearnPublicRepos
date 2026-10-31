<!-- Source: https://learn.microsoft.com/en-us/intune/app-management/configuration/manage-referenced-apps-aosp -->
<!-- Sitemap-Last-Modified: 2026-10-26 -->

# Manage AOSP referenced apps in Microsoft Intune

AOSP referenced apps identify apps by package name instead of an uploaded APK. You can use Microsoft Intune to manage OEM, preloaded, or externally deployed apps on Android Open Source Project \(AOSP\) devices. The app must already be on the device or be deployed outside Intune.

To unhide an existing app on the device, assign the referenced app as **Required**. To hide the app without deleting it, assign it as **Uninstall**. The **Available** assignment type isn't supported for referenced apps.

AOSP referenced apps support user-associated and userless AOSP devices.

## Before you start

- Make sure the devices are enrolled in Intune with AOSP user-associated or AOSP userless enrollment.
- Make sure the app is already on the devices, or arrange to deploy it outside Intune.
- Get the app's package name. If you don't know the package name, contact the device manufacturer or app vendor.
- Make sure you have permissions to create and assign apps in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). For permission guidance, see [Role-based access control](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

## Select the app type

Select the AOSP referenced app type to open the app creation steps. You don't need to upload an APK or select an app from Google Play.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **All apps** > **Create**.
3. For **Platform**, select **Android**.
4. For **Category**, select **Referenced apps**.
5. Select **AOSP referenced app**, and then select **Create**.

## Set app information

Enter the app details and the package name that Intune uses to identify the app on the device.

1. On the **App information** page, add the following details:

   - **Name**: Enter the name of the app as it appears in Intune.
   - **Publisher**: Enter the name of the app publisher.
   - **Package name**: Enter the package name of the app. Intune validates that the package name is valid.

2. Select **Next** to display the **Scope tags** page.

The package name can't be changed after you create the app. To manage a different package, create a new referenced app. If you don't know the package name, contact the device manufacturer or app vendor.

You can't create referenced apps for Company Portal \(`com.microsoft.windowsintune.companyportal`\) or Microsoft Authenticator \(`com.azure.authenticator`\).

## Select scope tags \(optional\)

Use scope tags to control which administrators can access the app in Intune. For more information, see [Use role-based access control and scope tags](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

1. Select **Select scope tags** to add scope tags for the app, if needed.
2. Select **Next** to display the **Assignments** page.

## Assign the app

Choose group assignments to unhide or hide the app on targeted devices. AOSP referenced apps support **Required** and **Uninstall** assignments only.

- **Required**: Unhides an existing, enabled app when needed. If a preinstalled system package is retained on the device but isn't installed for the current user, Intune can restore it for that user. Intune doesn't download a new APK. If the package isn't on the device, the assignment fails.
- **Uninstall**: Hides the app without removing its APK or app data, and without disabling it. If the app is absent or already hidden, the assignment is satisfied without further action.

Note

An app's hidden state is separate from its enabled state. Intune can unhide or restore an app, but it can't override a disabled state set by the user, device manufacturer, or another mechanism. A **Required** assignment fails until the app is enabled outside Intune.

1. Select the group assignments under **Required** or **Uninstall**.
2. Select **Next** to display the **Review + create** page.

Note

If an app doesn't have a launchable activity, its icon won't appear on the home screen, even when a **Required** assignment succeeds.

For group assignment guidance, see [Assign apps to groups](https://learn.microsoft.com/en-us/intune/app-management/deployment/assign-groups).

## Review and create the app

Review the app details before adding the referenced app to Intune.

1. Review the values and settings on the **Review + create** page.
2. Select **Create** to add the app to Intune.

The app's **Overview** page is displayed. The referenced app also appears in the apps list.

## Hide an existing referenced app

To hide an OEM, preloaded, or externally deployed app, assign the referenced app as **Uninstall**. The app's APK and data remain on the device.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **All apps**.
3. Select the AOSP referenced app from the apps list.
4. Select **Properties**, and edit **Assignments**.
5. Add the target group under **Uninstall** and remove its **Required** assignment, if one exists.
6. Review and save the assignments.

If another referenced-app **Required** assignment targets the same package on the device, it takes precedence over **Uninstall**. Removing a Required assignment alone doesn't hide the app.

## Related content

- [Manage Android Enterprise system apps](https://learn.microsoft.com/en-us/intune/app-management/configuration/manage-system-apps-android)
- [Configure apps on managed Android devices](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-android)
