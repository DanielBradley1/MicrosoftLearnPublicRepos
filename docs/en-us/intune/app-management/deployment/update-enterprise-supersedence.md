<!-- Source: https://learn.microsoft.com/en-us/intune/app-management/deployment/update-enterprise-supersedence -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Guided Update Supersedence for Enterprise App Management

Guided update supersedence for Enterprise App Management allows you to check for updates of Windows \(Win32\) Enterprise App Catalog apps. You can view an available update for the app and select the option to create a new app with a supersedence relationship for the app it’s updating. Prepopulated attributes are provided when creating the new app.

## View available updates

In the **Overview** pane for a selected Enterprise App Catalog app, you can view the available updates by selecting the tile **Enterprise App Catalog apps with available updates**.

Note

Microsoft has established Service Level Objectives \(SLOs\) for app update availability. Most app updates are available within 24 hours of vendor release, while those requiring manual validation typically become available within seven days. For details, see [Enterprise App Management overview](https://learn.microsoft.com/en-us/intune/app-management/deployment/enterprise-app-management).

The **Enterprise App Catalog apps with updates** pane provides a list of Enterprise App Catalog apps that can be updated. This list provides the following app details:

- **App name**: - The name of the app.
- **Publisher**: - The publisher of the app.
- **Provisioned version**: - The currently installed app version.
- **Latest available version**: - The new version that is available.

[![Screenshot the Enterprise App Catalog app list with available updates.](https://learn.microsoft.com/en-us/intune/app-management/deployment/media/update-enterprise-supersedence/apps-eam-supersedence-02.png)](https://learn.microsoft.com/en-us/intune/app-management/deployment/media/update-enterprise-supersedence/apps-eam-supersedence-02.png#lightbox)

## Update an Enterprise App Catalog app

1. To update an Enterprise App Catalog app, select the *app name* to display additional options.

   You can update a specific app. This option allows you to update the app with a newer app version. Intune uses information from the Enterprise App Catalog to define properties and settings. You can review and define custom settings as needed. You should consider downloading and exporting the properties of the app before updated.

   Superseding an app creates a new app with the latest app package and sets up the supersedence relationship. Some settings, such as scope tags and assignments won't be copied to the new app.
2. Select the **Update** option for the specific app. The **Update application** pane is displayed.

   [![Screenshot an Enterprise App Catalog app list the supersedence option.](https://learn.microsoft.com/en-us/intune/app-management/deployment/media/update-enterprise-supersedence/apps-eam-supersedence-04.png)](https://learn.microsoft.com/en-us/intune/app-management/deployment/media/update-enterprise-supersedence/apps-eam-supersedence-04.png#lightbox)
3. Select **Supersede app**.
4. Select your app **Assignments**, then **Review + create** the superseded app.

## Next steps

- [Microsoft Intune Enterprise Application Management](https://learn.microsoft.com/en-us/intune/app-management/deployment/enterprise-app-management)
- [Add an Enterprise App Catalog app to Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-enterprise-catalog-app)
- [Troubleshoot Win32 app issues](https://learn.microsoft.com/en-us/intune/app-management/deployment/troubleshoot-win32)
- [Monitor app information and assignments with Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/monitor-assignments)
