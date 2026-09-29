<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mobile-pretest-android -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Deploy Defender for Endpoint prerelease builds on Android devices using Google Play preproduction tracks

Learn how to setup a secure environment to safely test prerelease versions of Microsoft Defender for Endpoint on Android using Google Play preproduction tracks. This guide is useful for deploying prerelease builds or custom Defender for Endpoint Android Package Kit \(APK\) files to a limited number of users before fully deploying them to all users in your organization.

The following instructions explain how to set up your environment for prerelease testing or custom APK deployment. These steps are for Android devices that are onboarded to Microsoft Defender for Endpoint through the following methods:

- Android Enterprise scenarios
- Mobile Application Management \(MAM\) enrollment scenarios

> Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

## Set up your testing environment in the Android Enterprise scenario

To set up your environment for prerelease testing, follow these steps:

1. Contact Microsoft Support to provide the Google Play Store Organization ID for your organization and wait for confirmation. The ID is required to add your information to an inclusion list and make the prerelease build available for testing. You can find the Organization ID from the Microsoft Intune Admin center under **Apps > Android > Add - > App type > Managed Google Play** then selecting the icon on the top right corner. The following screenshot shows where to find the Organization ID icon in the Microsoft Intune admin center.

   [![Screenshot of Microsoft Intune admin center highlighting the org ID](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/icon-select-small.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/icon-select.png#lightbox)
2. Sync the managed Google Play app with Intune. See [Sync a Managed Google Play app with Intune](https://learn.microsoft.com/en-us/intune/intune-service/apps/apps-add-android-for-work#sync-a-managed-google-play-app-with-intune) for more information. The following screenshots show the sync process in the Microsoft Intune admin center:

   ![Screenshot selecting an app for managed Play in the Microsoft Intune admin center](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/intune-sync.png)

   ![Screenshot highlighting the Sync option in the Managed Play store](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/manage-sync.png)
3. Create a group in [Microsoft Intune Admin Center](https://intune.microsoft.com/).
4. In the Microsoft Intune admin center, navigate to **Apps > All apps** and search for *Microsoft Defender: Antivirus*.
5. In the **Properties** pane, select **Edit** beside **Assignments** and then add the user group under *Available for enrolled devices*.

   ![Screenshot highlighting the Microsoft Defender Antivirus properties](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/assignments-edit.png)
6. In the **Edit application** list, select the added group to open the **Edit assignment** pane.
7. In the Edit assignment pane, select **Included** as the mode. Then select **Custom testing track \(number\)** in the **Tracks** dropdown list. Then select default under **Update priority**.

   ![Screenshot of the required Edit assignment settings](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/edit-assign-settings.png)
8. Select **Review + save** to review and save the details.

After the app is synced and assigned to a user group, the following steps are required for the members of the user group to test the prerelease build on the Android device:

1. Open the Microsoft Intune Company Portal on the Android device and sign in with the user account that is part of the user group assigned to the prerelease build.
2. In the device's managed section, open the **Play Store** app and search for *Microsoft Defender: Antivirus*.
3. Select the app and then **Install** to install the prerelease build on the device.
4. Open the app and sign in with the user account that is part of the user group assigned to the prerelease build.
5. Follow the prompts to complete the onboarding process.

## Set up your testing environment in the MAM enrollment scenario

To set up your environment for prerelease testing, follow these steps:

1. Create a Google group for your organization, which is required to add your information to an inclusion list and make the prerelease build available to your group. To create a Google group, see [Create a group and choose group settings](https://support.google.com/groups/answer/2464926). The group you create appears in the Google Groups list. The following screenshot shows the Google group in the Google Groups list.

   ![Screenshot of highlighting the Google group added to the list](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/group-name.png)
2. Contact Microsoft Support to provide the Google group name for your organization then wait for confirmation. Then, send the [Google Play prerelease testing page link](https://play.google.com/apps/testing/com.microsoft.scmx?pli=1) to the members of the Google group so that they can download the prerelease build.
3. Users testing the prerelease build must sign in to the Google Play Store using the Google account that's part of the Google group.
4. Search and download the prerelease build from the [Google Play prerelease testing page](https://play.google.com/apps/testing/com.microsoft.scmx?pli=1). Users are then redirected to a *Welcome to the testing program* page and an install page for Microsoft Defender: Antivirus. The following screenshots show the testing program welcome page and the Microsoft Defender: Antivirus install page.

   ![Screenshot of a Welcome page to test the prelease build of Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/welcome-test.png)

   ![Screenshot of a prerelease version of Microsoft Defender Antivirus in the Google Play Store](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/beta-app.png)
5. Sign in to the Defender app using the work/corporate account. Then follow the prompts to complete the onboarding process.

   ![Screenshot of the Microsoft Defender Antivirus sign in page](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/defender-signin.png)
6. Once successfully onboarded, the app shows a label on top to indicate that the prerelease version is running. The following screenshot shows the label that indicates the prerelease version is running.

   ![Screenshot of a prerelease version of Microsoft Defender Antivirus installed on a device](https://learn.microsoft.com/en-us/defender-endpoint/media/mobile-pretest-android/preview-build.png)

Tip

If users in the Google group are unable to see or download the correct prerelease build, ensure that the user is a member of the Google group assigned to the prerelease build. You can also try syncing Google Play apps from the Microsoft Intune Admin center. Users can also try clearing the cache and data of the Google Play Store app on their Android device.
