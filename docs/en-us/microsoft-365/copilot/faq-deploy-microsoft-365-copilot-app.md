<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/faq-deploy-microsoft-365-copilot-app -->
<!-- Sitemap-Last-Modified: 2026-09-18 -->

# Frequently asked questions about deploying the Microsoft 365 Copilot app

**Microsoft 365 Copilot is now named Microsoft Copilot, and Microsoft 365 Copilot Chat is now named Microsoft Copilot Chat. This article applies to the former Microsoft 365 Copilot app. There are no changes to security, compliance, and privacy for organizations**.

The Microsoft 365 Copilot app helps Microsoft 365 users be more productive by providing a single place to access [Microsoft 365 Copilot](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-overview) features and capabilities, including search, chat, agents, and more.

Users can visit [Download the Microsoft 365 Copilot app](https://www.microsoft.com/en-US/microsoft-365-copilot/download-copilot-app) to download the app. The app is also available in the [Microsoft Store](https://apps.microsoft.com/detail/9wzdncrd29v9).

## What deployment methods are supported for the Microsoft 365 Copilot app on Windows?

- Deploy as a Microsoft Store app using [Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/apps/store-apps-microsoft).
- Deploy the Microsoft 365 Copilot app using deployment and management tools.

  Admins can deploy the Microsoft 365 Copilot app using software deployment and management solutions. For example:

  - [Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/apps/lob-apps-windows).
  - [Microsoft Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/introduction) via either a [Package](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/packages-and-programs) or an [Application](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/deploy-applications).
  - [Group Policy](https://learn.microsoft.com/en-us/troubleshoot/windows-server/group-policy/use-group-policy-to-install-software).
  - Non-Microsoft deployment and management solutions.


  The Microsoft 365 Copilot app stand-alone .EXE installer for use with the software deployment and management solutions can be downloaded from the following sources:


  - [Download the Microsoft 365 Copilot app](https://www.microsoft.com/en-US/microsoft-365-copilot/download-copilot-app).
  - [Microsoft Store](https://apps.microsoft.com/detail/9wzdncrd29v9).
  - [Downloaded directly](https://go.microsoft.com/fwlink/?linkid=2325486).

- Deploy the app automatically with Microsoft 365 Apps.

  Windows devices with commercial Microsoft 365 desktop apps automatically install the Microsoft 365 Copilot app. The installation happens in the background and doesn't interrupt the user.

  - To install, devices must have Microsoft 365 Apps Version 2511 or later. Version 2511 released to the Current Channel in early December 2025 and to the Monthly Enterprise Channel in January 2026.
  - Devices on the Semi-Annual Enterprise Channel don't automatically install the Microsoft 365 Copilot app.
  - Admins can opt out from automatic installation of the Microsoft 365 Copilot app in the [Microsoft 365 Apps admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/deploy-microsoft-365-copilot-app#prevent-automatic-installation).


  Note


  The installation of the Microsoft Copilot app to devices with Microsoft 365 Apps isn't enabled for customers in the European Economic Area \(EEA\).

- Deploy the app from the Microsoft 365 Content Delivery Network \(CDN\) directly.

  For organizations that disable access to the Microsoft Store, the installer can be downloaded directly from the Microsoft 365 CDN or can be [downloaded directly](https://go.microsoft.com/fwlink/?linkid=2325486).

## Where can the stand-alone EXE/MSI installer for the Microsoft 365 Copilot app be downloaded from?

The Microsoft 365 Copilot app can be downloaded from the following sources:

- [Download the Microsoft 365 Copilot app](https://www.microsoft.com/en-US/microsoft-365-copilot/download-copilot-app).
- [Microsoft Store](https://apps.microsoft.com/detail/9wzdncrd29v9).
- [Downloaded directly](https://go.microsoft.com/fwlink/?linkid=2325486).

## We don't have access to the Windows Store. How can the app be installed or updated?

The Microsoft Store isn't required to install the app with Microsoft 365 desktop apps suite or from the stand-alone .exe installer from the CDN.

The Microsoft 365 Copilot app can update automatically both through the Microsoft Store and its own built-in updater. If the Store isn't available, then the built-in updater uses the CDN as the update source.

To ensure reliable app installation, working, and delivery of updates, administrators should allow access to the below list of domains. These domains are used by Microsoft to distribute updates and content more efficiently.

| Endpoint | Notes |
| --- | --- |
| `*.office.net` | Microsoft 365 Content Delivery Network \(CDN\) used for install and updates. |
| `licensing.mp.microsoft.com` | Licensing servers. |
| `login.microsoftonline.com` | Required for licensing activation. |
| `*.displaycatalog.mp.microsoft.com` | Store catalog. |
| `storecatalogrevocation.storequality.microsoft.com` | Store app revocation. |
| `purchase.mp.microsoft.com` | Microsoft Store purchases. |

For a comprehensive list of Microsoft 365 URLs and IP address ranges, see [Microsoft 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges).

## How does the automatic deployment with the Microsoft 365 desktop apps work?

- The Microsoft 365 Copilot app is automatically installed on eligible Windows devices that have installations of the commercial Microsoft 365 desktop apps.

  - Requires Microsoft 365 Apps to be on Current Channel or Monthly Enterprise Channel.
  - Doesn't apply to tenants in the European Economic Area \(EEA\).
  - Admins can opt out from automatic installation in the [Microsoft 365 Apps admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/deploy-microsoft-365-copilot-app#prevent-automatic-installation).

- The app appears in the **Start** menu as a new entry point for accessing the Copilot experiences across Microsoft 365. On devices where the app is already installed, no visible change occurs.
- Review [Deployment overview for the Microsoft 365 Copilot app](https://learn.microsoft.com/en-us/microsoft-365/copilot/deploy-microsoft-365-copilot-app) for more details and instructions on how to manage automatic deployments.

## Is the automatically installed Microsoft 365 Copilot app different from the Microsoft 365 Copilot app installed via the Suite installer? If not, how does it affect devices where the Microsoft 365 Copilot app is already deployed via a deployment and management tool?

The automatically installed Microsoft 365 Copilot app is the same app as the one installed using other deployment and management solutions. If the Microsoft 365 Copilot app is installed already, there's no effect when attempting to install again via either from a deployment and management tool or the Microsoft 365 Apps suite.

## Is there any effect to the existing functionalities of the Microsoft 365 Copilot app if the app is automatically installed through the Microsoft 365 desktop apps?

If the Microsoft 365 Copilot app is already installed, the app is updated to the latest version.

## How does the rollout process work for installing or updating the Microsoft 365 Copilot app through the Microsoft 365 Suite?

As documented at [Deployment overview for the Microsoft 365 Copilot app](https://learn.microsoft.com/en-us/microsoft-365/copilot/deploy-microsoft-365-copilot-app), the installation requires the device to have Microsoft 365 Apps Version 2511 or later.

Note

Version 2511 or later of Microsoft 365 Apps is a prerequisite for the automatic installation of the Microsoft 365 Copilot app. The installation of the Microsoft 365Copilot app happens after the device installs or updates to Version 2511 or later of Microsoft 365 Apps. After Microsoft 365 Apps is installed or updated to version 2511 or later, it might take up to seven days for the install or upgrade of the Microsoft 365 Copilot app to occur.

## How does Microsoft discover if a user is in the European Economic Area \(EEA\). How is a user excluded? What are the differences if the Microsoft 365 Copilot app is rolled out manually?

- The attributes of the tenant determine whether a user is considered EEA or non-EEA. For example, a US-based customer with an end user device in France would be eligible. A France-based customer with an end user device in USA wouldn't be eligible.
- Customers in the EEA or non-EEA can choose to roll out the Microsoft 365 Copilot app manually by targeting user groups. For more information, follow the guidelines at [Deployment overview for the Microsoft 365 Copilot app](https://learn.microsoft.com/en-us/microsoft-365/copilot/deploy-microsoft-365-copilot-app).

## What is the recommendation for managing installation and updates for Microsoft 365 Copilot app for European Economic Area \(EEA\) customers?

Microsoft 365 Copilot app installs and updates EEA customers like non-EEA customers. The difference is how the Microsoft 365 Copilot app gets installed:

- In EEA the Microsoft 365 Copilot app only installs from the Microsoft Store or CDN.
- In non-EEA, the Microsoft 365Copilot app can also be installed with Microsoft 365 Apps Suite.

## If the Microsoft 365 Copilot app is initially deployed to a device in the user-context, what's the behavior when the app is automatically installed through the Microsoft 365 Apps on the device?

The automatic installation of the Microsoft 365 Copilot app happens in the **SYSTEM** context so therefore is provisioned system wide. If a device already has a user-context deployment of Microsoft 365 Copilot app, after the Microsoft 365 Apps suite installation, the Microsoft 365 Copilot app is provisioned system-wide. The users that already had the Microsoft 365 Copilot app continue to have the app. Other users on the device that previously didn't have the Microsoft 365 Copilot app now also have the app available for their use.

When the Microsoft 365 Copilot app installs in the **SYSTEM** context, there's only one instance of the Microsoft 365 App on the device. There aren't duplicate instances per user of the app on the device.

The stand-alone .EXE installer method can also deploy the Microsoft 365 Copilot app in the **SYSTEM** context, including through [Microsoft Intune and Microsoft Configuration Manager](https://learn.microsoft.com/en-us/microsoft-365/copilot/deploy-microsoft-365-copilot-app).

## If the Microsoft 365 Copilot app is automatically installed with Microsoft 365 Suite and a user on a device later uninstalls it, is it automatically reinstalled again?

No. The automatic installation of the Microsoft 365Copilot app with Microsoft 365 Apps happens only once. If a user uninstalls the Microsoft 365 Copilot app, then they must take action to reinstall the app.

## Is the "Microsoft 365" App automatically be upgraded to the "Microsoft 365 Copilot" App or is a new standalone Microsoft 365 Copilot app installed?

If the Microsoft Office version of the app is installed, the app is updated to reflect the newer version with the app name change. Depending on eligibility, additional functionalities are added.

## Is there a minimum Microsoft 365 Copilot app version to update without depending on the Microsoft Store?

Versions of the Microsoft 365 Copilot app after 19.2510.42021.0 can update from the Microsoft 365 Content Delivery Network \(CDN\) without the Microsoft Store dependency when installed through the suite installer or the stand-alone .EXE installer. Older versions of the app can't update without the Microsoft Store dependency.

## Are Microsoft 365 Apps devices affected if they are on the Semi-Annual Enterprise Channel?

No. The automatic installation of the Microsoft 365 Copilot app doesn't target devices on the Semi-Annual Enterprise Channel.
