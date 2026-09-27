<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/configure-apps -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Configure applications with Microsoft Intune

With Intune, school IT administrators have access to diverse applications to help students unlock their learning potential. This section discusses tools and resources for adding apps to Intune.

Applications can be assigned to groups:

- If you target apps to a **group of users**, the apps will be installed on any managed devices that the users sign in to.
- If you target apps to a **group of devices**, the apps will be installed on those devices and available to any user who signs in.

## Add apps

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Add applications to your inventory

- [Intune](#tabpanel_1_intune)
- [Intune For Education](#tabpanel_1_intune-for-education)

Intune supports the deployment several application types including desktop apps \(msi, exe\), Microsoft Store apps, web apps, appxbundle and MSIX.

#### Enterprise Application Management

Enterprise App Management enables you to easily discover and deploy applications and keep them up to date from the Enterprise App Catalog. The Enterprise App Catalog is a collection of prepared Microsoft and non-Microsoft applications. These apps are Win32 apps that are [prepared as Win32 apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/create-win32-package) and hosted by Microsoft.

Important

Enterprise App Management is part of Microsoft Intune Suite and available for trial and purchase. For more information, see [Microsoft Intune advanced capabilities](https://learn.microsoft.com/en-us/intune/fundamentals/advanced-capabilities).

For more information, see [Enterprise Application Management](https://learn.microsoft.com/en-us/intune/app-management/deployment/enterprise-app-management).

#### Win32 apps \(MSI, exe\)

The addition of desktop applications to Intune should be carried out by repackaging the apps, and defining the commands to silently install them. The process is described in the article [Add, assign, and monitor a Win32 app in Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-win32).

#### Microsoft Store app \(new\)

To create Microsoft Store apps in Intune:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Apps** > **All Apps** > **Create**.
2. In **Select app type** pane, select **Microsoft Store app \(new\)** under the **Store app** section.
3. Choose **Select** at the bottom of the page to begin creating an app from the Microsoft Store. The app creation experience has three steps:

   - App information
   - Assignments
   - Review + create

4. Select **Search the Microsoft Store app** to search for and select the app.
5. Review and change settings as required.

   Note

   Most administrators choose to deploy store apps in the **system** context on education devices for the fastest installation to all users of a device.
6. Select **Save**.

For more information, see [Add Microsoft Store apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-microsoft-store).

#### Web apps

To create web applications in Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **All Apps** > **Create**.
3. In the **Select app type** pane, under the **Other** types, select **Windows web link**.
4. Click **Select**. The **Add app** steps are displayed.
5. Provide a URL for the web app, a name, and optionally an icon and description.
6. Select **Save**

For more information, see [Add web apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-web).

Intune for Education supports the deployment of two types of Windows applications: **web apps** and **desktop apps**.

[![Intune for Education - Apps](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/configure-apps/intune-education-apps.png)](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/configure-apps/intune-education-apps.png#lightbox)

#### Desktop apps

Intune for Education supports:

- **Single file MSI** - Single file MSI files can be uploaded directly to Intune for Education. For more information, see [Add desktop apps in Intune for Education](https://learn.microsoft.com/en-us/intune-education/add-desktop-apps-edu).
- **Win32 apps** - The addition of desktop applications to Intune should be carried out by repackaging the apps, and defining the commands to silently install them. The process is described in the article [Add, assign, and monitor a Win32 app in Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-win32).

Note

For consistency, it is recommended that you choose to use only one of the desktop app installation methods. For example, if you have any applications that require the use of the Win32 app capability, then package and deploy all apps using the Win32 apps capability and don't use the single file MSI \(LOB\) option.

#### Web apps

To create web applications in Intune for Education:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Apps**.
3. Select **New app** > **New web app**.
4. Provide a URL for the web app, app name, and optionally an icon and description.
5. Select **Save**.

For more information, see [Add web apps](https://learn.microsoft.com/en-us/intune-education/add-web-apps-edu).

#### Microsoft Store app \(new\)

To create Microsoft Store apps in Intune for Education:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Apps**.
3. Select **New app** > **New Microsoft Store app \(new\)**.
4. Search for and select the app.
5. Review and change settings as required.

   Note

   Most customers choose to deploy store apps in the **system** context on education devices for the fastest installation to all users of a device.
6. Select **Save**.

For more information, see [Add Microsoft Store apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-microsoft-store).

Tip

The best user experience for receiving apps on a device is for apps to be assigned using Apple School Manager and the Volume Purchase Program \(VPP\) with device licensing. When device-licensed VPP apps are assigned to devices or users, the app can be installed without user interaction. For iOS apps without VPP, the user is prompted to sign in to the App Store with an Apple ID.

- [Intune](#tabpanel_2_intune)
- [Intune For Education](#tabpanel_2_intune-for-education)

#### Volume purchase program \(VPP\) apps

To add apps from VPP, set up a connection to Apple School Manager and add your apps in Apple School Manager.

For more information, see [Configure VPP tokens](https://learn.microsoft.com/en-us/intune/app-management/deployment/manage-vpp-apple).

#### iOS App

To add apps to iOS devices without using VPP in Intune for Education:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **All Apps** > **Create**.
3. In the **Select app type** pane, select **iOS store app**.
4. Click **Select**. The **Add app** steps are displayed.
5. Select **Search the App Store**.
6. In the **Search the App Store** pane, select the App Store country/region locale.
7. In the **Search** box, type the name \(or part of the name\) of the app. Intune searches the store and returns a list of relevant results.
8. In the results list, select the app you want, and then select **Select**.
9. Follow the steps remaining steps and select **Create**.

Note

Apps installed with this method will require the user of the device to sign in using an Apple ID to install the application. To avoid prompting the user for an Apple ID, use VPP apps.

#### Web apps

To create web applications:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **All Apps** > **Create**.
3. In the **Select app type** pane, under the **Other** types, select **iOS/iPadOS web clip**.
4. Click **Select**. The **Add app** steps are displayed.
5. Follow the steps remaining steps and select **Create**.

For more information, see [Add web apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-web).

#### Volume purchase program \(VPP\) apps

To add apps from VPP, set up a connection to Apple School Manager and add your apps in Apple School Manager.

For more information, see [Configure VPP tokens](https://learn.microsoft.com/en-us/intune-education/setup-ios-device-management#configure-vpp-tokens).

#### iOS App

To add apps to iOS devices without using VPP in Intune:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Apps**.
3. Select **New app** > **New iOS app**.
4. Search the app store by entering the app name and selecting the country.
5. Select the app in the list.
6. Click **Add to Intune**.

Note

Apps installed with this method will require the user of the device to sign in using an Apple ID to install the application. To avoid prompting the user for an Apple ID, use VPP apps.

#### Web apps

To create web applications in Intune for Education:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Apps**.
3. Select **New app** > **New web app**.
4. Provide a URL for the web app, a name, and optionally an icon and description.
5. Select **Save**.

For more information, see [Add web apps](https://learn.microsoft.com/en-us/intune-education/add-web-apps-edu).

### Other apps

Intune also supports deploying **[iOS/iPadOS LOB apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-lob-ios)** from the Intune admin center. A line-of-business \(LOB\) app is an app that you add to Intune from an IPA app installation file.

## Assign apps

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Assign apps from your inventory to groups

- [Intune](#tabpanel_3_intune)
- [Intune For Education](#tabpanel_3_intune-for-education)

To assign applications to a group of users or devices:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **All Apps**.
3. In the **Apps** pane, select the app you want to assign.
4. In the **Manage** section of the menu, select **Properties**.
5. Next to assignments, select **Edit**.
6. Select one or more groups to for the app assignment and select **Select**.
7. Review your selections and select **Save**.

To assign applications to a group of users or devices:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Groups** > Pick a group to manage.
3. Select **Apps**.
4. Select either **Web apps** or **Windows apps**.
5. Select the apps you want to assign to the group > **Save**.

- [Intune](#tabpanel_4_intune)
- [Intune For Education](#tabpanel_4_intune-for-education)

To assign applications to a group of users or devices:

1. 

   1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Apps** > **All Apps**.
3. In the **Apps** pane, select the app you want to assign.
4. In the **Manage** section of the menu, select **Properties**.
5. Next to assignments, select **Edit**.
6. Select one or more groups to for the app assignment and select **Select**.
7. Review your selections and select **Save**.

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Groups** > Pick a group to manage.
3. Select **Apps**.
4. Select either **Web apps** or **iOS apps**.
5. Select the apps you want to assign to the group > **Save**.

## Next steps

With the applications configured, you can now deploy students' and teachers' devices.

[Next: Deploy devices >](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/enroll-overview)
