<!-- Source: https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-chrome-android -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Configure Google Chrome for Android Devices Using Intune

You can use an Intune app configuration policy to configure Google Chrome for Android devices. The settings for the app can be automatically applied. For example, you can specifically set the bookmarks and the URLs that you would like to block or allow.

## Prerequisites

- The user's Android Enterprise device must be enrolled in Intune. For more information, see [Set up enrollment of Android Enterprise personally-owned work profile devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-personal-work-profile).
- Google Chrome is added as a Managed Google Play app. For more information about Managed Google Play, see [Connect your Intune account to your Managed Google Play account](https://learn.microsoft.com/en-us/intune/device-enrollment/android/connect-managed-google-play).

## Add the Google Chrome app to Intune

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **All Apps** > **Create** then add the **Managed Google Play** app.
3. Go to Managed Google Play, search with **Google Chrome** and approve.

   ![Search and approve Google Chrome](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/search.png)

4. Assign Google Chrome to a group as a required app type. Google Chrome is deployed automatically when the device is enrolled into Intune.

For more information about adding a Managed Google Play app to Intune, see [Managed Google Play store apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-managed-google-play#managed-google-play-store-apps).

## Add app configuration for managed AE devices

1. From the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Apps** > **Configuration** > **Create** > **Managed devices**.
2. Set the following details:

   - **Name** - The name of the profile that appears in the portal.
   - **Description** - The description of the profile that appears in the portal.
   - **Device enrollment type** - This setting is set to **Managed devices**.
   - **Platform** - Select **Android**.


   ![Add Google Chrome Configuration policy](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/add-policy.png)

3. Select **Associated app** to display the **Associated app** pane. Find and select **Google Chrome**. This list contains [Managed Google Play apps that you've approved and synchronized with Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-managed-google-play).

   ![Select Google Chrome under Associated app](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/associated-app.png)

4. Select **Configuration settings**, select **Use configuration designer**, and then select **Add** to select the configuration keys.

   ![Add Use configuration designer](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/configuration.png)


   Below is the example of the common settings:


   - **Block access to a list of URLs**: `["*"]`
   - **Allow access to a list of URLs**: `["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
   - **Managed Bookmarks**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
   - **Incognito mode availability**: `Incognito mode disabled`


   Once the configuration settings are added using the configuration designer, they'll be listed in a table.


   ![Common settings](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/common-settings.png)


   The above settings create bookmarks and block access to all URLs except `baidu.com`, `youtube.com`, `chromium.org`, and `chrome://`.

5. Select **OK** and **Add** to add your configuration policy to Intune.
6. Assign this configuration policy to a user group. For more information, see [Assign apps to groups with Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/assign-groups).

## Verify the device settings

Once the Android device is enrolled with Android Enterprise, the managed Google Chrome app with the portfolio icon will be deployed automatically.

![Managed Google Chrome with the portfolio icon](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/chrome-icon.png)

Launch Google Chrome and you'll find the settings applied.

Bookmarks:  
![View bookmarks](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/bookmarks.png)

Blocked URL:  
![Blocked URL](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/blocked-url.png)

Allow URL:  
![Allow URL](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/allowed-url.png)

Incognito tab:  
![Incognito tab](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/incognito-tab.png)

## Troubleshooting

1. Check Intune to monitor the policy deployment status.

   ![Monitor the policy deployment status](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/monitor-status.png)

2. Launch Google Chrome and visit **chrome://policy**. We can confirm if the settings are applied successfully.

   ![Confirm settings are applied successfully](https://learn.microsoft.com/en-us/intune/app-management/configuration/media/configure-chrome-android/confirm.png)

## Additional information

- [Add app configuration policies for managed Android Enterprise devices](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-android)
- [Chrome Enterprise policy list](https://cloud.google.com/docs/chrome-enterprise/policies/)

## Next steps

- For more information about Android Enterprise fully managed devices, see [Set up Intune enrollment of Android Enterprise fully manage devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-fully-managed).
