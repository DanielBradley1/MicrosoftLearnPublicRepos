<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/deploy-microsoft-365-copilot-app -->
<!-- Sitemap-Last-Modified: 2026-09-18 -->

# Deployment overview for the Microsoft 365 Copilot app

Note

Microsoft 365 Copilot is now named Microsoft Copilot, and Microsoft 365 Copilot Chat is now named Microsoft Copilot Chat. This article applies to the former Microsoft 365 Copilot app. There are no changes to security, compliance, and privacy for organizations.

The Microsoft 365 Copilot app deployment overview explains how IT admins can install and deploy the Microsoft 365 Copilot app to users and devices across an organization. It also covers Intune deployment, automatic installation with Microsoft 365 Apps, and how to prevent automatic installation.

## Download and install the app for a single user/device

The app is available as:

- A [Web app](https://m365.cloud.microsoft/)
- A desktop app that you can install on [Windows and Mac Devices](https://www.microsoft.com/microsoft-365/copilot/download-copilot-app)
- An Android app for [Android devices](https://support.microsoft.com/office/microsoft-365-copilot-app-for-android-0383d031-a1c6-46c9-b734-53cd1d22765b).
- An iOS app for [iOS devices](https://support.microsoft.com/office/microsoft-365-copilot-app-for-ios-c8880c05-883a-46b6-ad32-9bffa31228d0).

To install the app for a single user, follow these steps:

1. Download the [.exe installer](https://get.microsoft.com/installer/download/9WZDNCRD29V9).
2. Go to the location where you downloaded the `.exe` file.
3. Run the downloaded installer manually to install the app.

   ```powershell
   .\Microsoft 365 Copilot Installer.exe
   ```

For organizations that disable access to the Windows Store, the installer can be directly accessed from the [Microsoft 365 Content Delivery Network \(CDN\) link](https://go.microsoft.com/fwlink/?linkid=2325486).

### Install on a single device

To install on a single device, follow these steps:

1. Download the [.exe installer](https://go.microsoft.com/fwlink/?linkid=2325486).
2. Launch PowerShell 7 as administrator \(Run as Administrator\).
3. Navigate to the location where the `Setup.exe` file is located.
4. Run the following command:

   ```powershell
   .\M365CopilotDesktopInstaller.exe --quiet --start -p
   ```

## Deploy the app across your organization using software management tools

To deploy the Microsoft 365 Copilot app to a group of computers or your entire organization through Microsoft Intune, follow the steps in the article [Add Microsoft Store Apps to Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/apps/store-apps-microsoft).

Note

This method works regardless of whether the Microsoft Store is enabled or disabled for the user.

### Deploy via any MDM

To deploy the Microsoft 365 Copilot app to a group of devices, or your entire organization through any MDM:

1. Download the [.exe installer](https://go.microsoft.com/fwlink/?linkid=2325486).
2. Distribute the installer using [Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/what-is-intune), [Microsoft Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/introduction), [Group Policy](https://learn.microsoft.com/en-us/troubleshoot/windows-server/group-policy/use-group-policy-to-install-software), or a non-Microsoft software deployment solution.
3. Run the installer on each device to install the Microsoft 365 Copilot app.

## Deploy the app automatically with Microsoft 365 Apps

Windows devices with the Microsoft 365 desktop apps automatically install the Microsoft 365 Copilot app. The installation happens in the background and doesn't interrupt the user.

To install, devices must have Microsoft 365 Apps Version 2511. Version 2511 was released in the Current Channel in early December 2025 and in the Monthly Enterprise Channel in January 2026.

Devices on the Semi-Annual Enterprise Channel don't automatically install the Microsoft 365 Copilot app.

Note

The installation of the Microsoft 365 Copilot app to devices with Microsoft 365 Apps isn't enabled for the following:

- Customers in the European Economic Area \(EEA\)
- Government customers \(GCC, GCC High and DoD\)

### Prevent automatic installation

To prevent the app from installing on devices with existing installations of Microsoft 365 Apps:

1. Sign in to the [Microsoft 365 Apps admin center](https://config.office.com/officeSettings) with an account that has the right permissions.

   Tip

   Make sure you sign in to the Microsoft 365 **Apps** admin center and not the Microsoft 365 admin center. You can reach the Microsoft 365 Apps admin center from the Microsoft 365 admin center by selecting **Show all** > **All admin centers** > **Microsoft 365 app**.
2. From the left navigation bar, select **Customization**.
3. Under **Customization**, select [**Device Configuration**](https://config.office.com/officeSettings/configurations).
4. In the **Deployment configurations** page, select the **Modern Apps settings** tab.
5. In the list of modern apps, select **Microsoft 365 Copilot app**.
6. In the **Microsoft 365 Copilot app** pane, clear the **Enable automatic installation of Microsoft 365 Copilot app** check box.
7. Select **Save**.

## Update the Microsoft 365 Copilot app

The Microsoft 365 Copilot app can update automatically through the Microsoft Store and through its own built-in updater.

To ensure reliable app installation, functioning, and delivery of updates, administrators should allow access to the following list of domains. These domains are used by Microsoft to distribute updates and content more efficiently.

| Endpoint | Notes |
| --- | --- |
| `*.office.net` | Microsoft 365 CDN used for install and updates |
| `licensing.mp.microsoft.com` | Licensing servers |
| `login.microsoftonline.com` | Required for licensing activation |
| `*displaycatalog.mp.microsoft.com` | Store catalog |
| `storecatalogrevocation.storequality.microsoft.com` | Store app revocation |
| `purchase.mp.microsoft.com` | Microsoft Store purchases |

For a comprehensive list of Microsoft 365 URLs and IP address ranges, see [Microsoft 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges).

## Related content

- [Frequently asked questions about deploying the Microsoft 365 Copilot app](https://learn.microsoft.com/en-us/microsoft-365/copilot/faq-deploy-microsoft-365-copilot-app).
