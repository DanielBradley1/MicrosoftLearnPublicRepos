<!-- Source: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-company-portal-android -->
<!-- Sitemap-Last-Modified: 2026-04-08 -->

# Enroll your device with Company Portal

Enroll your personal or corporate-owned Android device with Intune Company Portal to get secure access to company email, apps, and data.

## Prerequisites

The Intune Company Portal app supports devices running Android 8.0 and later, including devices secured by Samsung Knox Standard 2.4 and later. To learn how to update your Android device to meet requirements, see [Check & update your Android version](https://support.google.com/android/answer/7680439).

Important

Support for Android Company Portal versions earlier than 5.0.5421.0 ended on October 1, 2025. Devices running older versions might no longer maintain their registration status and can be marked noncompliant. To keep devices registered and compliant, users must update to a supported version of the Company Portal app.

<iframe src="https://www.youtube-nocookie.com/embed/k0Q_sGLSx6o" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Note

Samsung Knox is a type of security that certain Samsung devices use for extra protection outside of what native Android provides. To check if you have a Samsung Knox device, go to **Settings** > **About device**. If you don't see the **Knox version** listed there, you have a native Android device.

## Install Company Portal app

Install the Intune Company Portal app [from Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). See [Install Company Portal app in People's Republic of China](https://learn.microsoft.com/en-us/intune/user-help/company-portal/install-android-china) for a list of stores that offer the app in People's Republic of China.

1. On your device, open the **Play Store** app.
2. Search for and install **Intune Company Portal**.
3. When prompted about app permissions, tap **ACCEPT**.

## Enroll device

During enrollment, you might be asked to choose a category that best describes how you use your device. Company Portal uses your answer to check for work and school apps relevant to you.

1. Open the Company Portal app and sign in with your work or school account. Review notification permissions for Company Portal as they pop up. You can adjust notification permissions anytime in the Settings app.
2. If you're prompted to accept your organization's terms and conditions, tap **ACCEPT ALL**.

   ![Screenshot of the Company Portal, Terms screen, highlighting "Accept all" button.](https://learn.microsoft.com/en-us/intune/user-help/enrollment/media/enroll-company-portal-android/accept-terms-1911.png)

3. Review what your organization can and can't see. Then tap **CONTINUE**.

   ![Screenshot of Company Portal, We care about your privacy screen, highlighting the Continue button.](https://learn.microsoft.com/en-us/intune/user-help/enrollment/media/enroll-company-portal-android/android-privacy-screen-1911.png)

4. Review what to expect in the upcoming steps. Then tap **NEXT**.

   ![Screenshot of Company Portal, What's next screen, highlighting the Next button.](https://learn.microsoft.com/en-us/intune/user-help/enrollment/media/enroll-company-portal-android/android-whats-next-1911.png)

5. Depending on your version of Android, you might be prompted to allow access to certain parts of your device. These prompts are a Google requirement and not controlled by Microsoft.

   Tap **Allow** for the following permissions:

   - **Allow Company Portal to make and manage phone calls**: This permission enables your device to share its international mobile station equipment identity \(IMEI\) number with Intune, your organization's device management provider. It's safe to allow this permission. Microsoft never makes or manages phone calls.
   - **Allow Company Portal to access your contacts**: This permission lets the Company Portal app create, use, and manage your work account. It's safe to allow this permission. Microsoft never accesses your contacts.


   If you deny permission, you'll be prompted again the next time you sign in to Company Portal. To turn off these messages, select **Never ask again**. To manage app permissions, go to the Settings app > **Apps** > **Company Portal** > **Permissions** > **Phone**.

6. Activate the device admin app.

   Company Portal needs device administrator permissions to securely manage your device. Activating the app lets your organization identify possible security issues, such as repeated failed attempts to unlock your device, and respond appropriately.

   ![Screenshot of the Activate device administrator screen, highlighting the activate button.](https://learn.microsoft.com/en-us/intune/user-help/enrollment/media/enroll-company-portal-android/activate-device-administrator-1911.png)

Note

Microsoft doesn't control the messaging on this screen. We understand that its phrasing can seem drastic. Company Portal can't specify which restrictions and access are relevant to your organization. If you have questions about how your organization uses the app, contact your IT support person. Go to the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) to find your organization's contact information.

7. Your device begins enrolling. Review and acknowledge the ELM Agent privacy policy if Company Portal prompts for it.
8. On the **Company Access Setup** screen, check that your device is enrolled. Then tap **CONTINUE**.

   ![Screenshot of Company Portal, Company Access Setup screen, showing Get your device managed is complete.](https://learn.microsoft.com/en-us/intune/user-help/enrollment/media/enroll-company-portal-android/update-settings-1911.png)

9. Your organization might require you to update your device settings. Tap **RESOLVE** to adjust a setting. When you're done updating settings, tap **CONTINUE**.

   ![Screenshot of Company Portal, Update device settings, highlighting Resolve and Continue buttons.](https://learn.microsoft.com/en-us/intune/user-help/enrollment/media/enroll-company-portal-android/resolve-settings-1911.png)

10. When setup is complete, tap **DONE**.

    ![Screenshot of Company Portal, Company Access Setup screen, showing completed setup and highlighting Done button.](https://learn.microsoft.com/en-us/intune/user-help/enrollment/media/enroll-company-portal-android/android-enrollment-done-1911.png)

## Next steps

Before you try to install a school or work app, modify device settings to allow app installations from unknown sources. If you don't make this change on your device, Company Portal blocks app installations. Open the **Settings** app on your device. Then go to **Security and privacy** > **Install unknown apps**.

If you get an error while you try to enroll your device in Intune, you can [email your company support](https://learn.microsoft.com/en-us/intune/user-help/diagnostics/collect-logs-android).

Still need help? Contact your company support. For contact information, check the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).
