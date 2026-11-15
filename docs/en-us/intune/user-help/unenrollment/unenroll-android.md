<!-- Source: https://learn.microsoft.com/en-us/intune/user-help/unenrollment/unenroll-android -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Remove device from Company Portal for Android

Remove an enrolled device so that your organization no longer manages it. After you remove the device from Company Portal:

- The device loses access to your organization's internal apps and websites.
- The device no longer appears in Company Portal. This change applies to enrolled devices and devices you set up just to access work emails.
- You can no longer install apps in Company Portal.
- Your organization no longer enforces setting requirements and restrictions, such as device PIN, disabling the camera, or prohibiting screenshots.

Note

This article is for devices set up by using the [Intune Company Portal app for Android](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). It doesn't apply to devices enrolled by using the [Microsoft Intune app](https://play.google.com/store/apps/details?id=com.microsoft.intune). You can't unenroll or remove a corporate-owned device by using the Microsoft Intune app.

## Remove device in Company Portal app

1. Sign in to the Company Portal app with your work account.
2. Select **Devices** and then select the device you want to remove.

   ![Screenshot of Company Portal app, highlighting a device called My Android.](https://learn.microsoft.com/en-us/intune/user-help/unenrollment/media/unenroll-android/remove-device-from-company-portal-2101-01.png)
3. From the menu, select **Remove Device**.

   ![Screenshot of Company Portal app, highlighting the menu button and Remove Device option.](https://learn.microsoft.com/en-us/intune/user-help/unenrollment/media/unenroll-android/remove-device-from-company-portal-2101-02.png)
4. Select **OK** to finish removing your device.

   ![Screenshot of Company Portal app, Remove this device confirmation, highlighting the OK option.](https://learn.microsoft.com/en-us/intune/user-help/unenrollment/media/unenroll-android/remove-device-from-company-portal-2101-03.png)

## Disable Company Portal device management

You can remove your device from management by disabling the Company Portal app. After disabling the app, you can uninstall it from your device.

1. Sign in to Company Portal.
2. Select the main menu.

   ![Screenshot of Company Portal app, highlighting the menu button.](https://learn.microsoft.com/en-us/intune/user-help/unenrollment/media/unenroll-android/remove-intune-company-portal-android-2101-01.png)
3. Select **Remove Company Portal**.

   ![Screenshot of Company Portal app, highlighting Remove Company Portal option in menu.](https://learn.microsoft.com/en-us/intune/user-help/unenrollment/media/unenroll-android/remove-intune-company-portal-android-2101-02.png)
4. Select **OK** to remove Company Portal and unenroll the device you're on.

   ![Screenshot of Company Portal app, Remove Company Portal confirmation, highlighting the OK option.](https://learn.microsoft.com/en-us/intune/user-help/unenrollment/media/unenroll-android/remove-intune-company-portal-android-2101-03.png)

Note

If you plan to use the app again, you can temporarily disable it without uninstalling it. After you re-enable the app, you must also re-enroll your device.

## Uninstall the Company Portal app

Company Portal is a device management app, so you can't uninstall it until you remove your device from management. After you remove the device, select and hold the Company Portal app icon until the app menu appears. Then select **Uninstall** to remove the app.

Alternatively, go to your device **Settings** > **Apps** and select **Company Portal** > **Uninstall**.

## Remove the Company Portal app as a device administrator

As a last resort, you can remove the Company Portal app as a device administrator. When you remove the app as a device administrator, you can unenroll your device and uninstall the app.

Tip

If you decline the Microsoft terms of use when signing in to the Company Portal app, you block all subsequent sign-in attempts. To remove the app as a device administrator and uninstall the app, follow the steps in this section. If you didn't mean to decline the Microsoft terms of use, you can reinstall the app and start over.

Device administrator settings might appear differently on your device. Use the option that aligns with your device experience.

**Option 1**:

1. Go to device **Settings** > **Security** > **Additional Security Settings** > **Device Administrators**.
2. Clear the **Company Portal** selection.

**Option 2**:

1. Select **Settings** > **Security and privacy** > **Other security settings** > **Device admin apps**.
2. Clear the **Company Portal** selection.
3. Follow the onscreen prompts to remove Company Portal and your work profile.

## Remove data collected by the Company Portal app

To remove all data that the Company Portal app for Android stores on your device:

1. Clear app data.

   1. Go to device **Settings** > **Apps**.
   2. Select **Company Portal** > **Clear data**.

2. Delete the following folder from your device: **\\storage\\internal storage\\Android\\data\\com.microsoft.windowsintune.companyportal**

### Effects of removing required apps

If you have a company-owned device, your organization might require Company Portal on your device. If you uninstall it, you could lose access to protected work resources such as email, apps, Wi-Fi, or VPN. You can regain access by reinstalling the app and enrolling your device.

## Next steps

Still need help? Contact your IT support person. For contact information, sign in to the Company Portal app and select the **Support** tab. You can also access helpdesk information on the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).
