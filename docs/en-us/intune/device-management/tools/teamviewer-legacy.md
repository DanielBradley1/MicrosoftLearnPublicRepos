<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/tools/teamviewer-legacy -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# Use TeamViewer to remotely administer Intune devices

Important

A new TeamViewer remote assistance experience is available in Intune and replaces the connector described in this article.

This article describes the previous TeamViewer connector, which is being deprecated. We recommend using the new TeamViewer integration for the latest experience and ongoing support. For more information and setup guidance, see [Use the TeamViewer integration in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-management/tools/setup-teamviewer).

Devices managed by Intune can be administered remotely using [TeamViewer](https://www.teamviewer.com). TeamViewer is a partner program that you purchase separately. This article shows you how to configure TeamViewer within Intune, and how to remotely administer a device.

This feature applies to:

- Android device administrator \(DA\)
- Android Enterprise personally owned devices with a work profile \(BYOD\)
- iOS/iPadOS
- macOS
- Windows

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Prerequisites

- The administrator configuring the TeamViewer connector must have an Intune license. You can give administrators access to Microsoft Intune without them requiring an Intune license. For more information, see [Unlicensed admins](https://learn.microsoft.com/en-us/intune/fundamentals/licensing#unlicensed-admin-access).
- Users must be assigned the Remote assistance connectors/Read and Remote assistance connectors/Update permissions in the Intune admin center to onboard TeamViewer. For more information, see [Role-based access control \(RBAC\) with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).
- Use a supported Intune-managed device:

  - Android device administrator \(DA\)
  - Android Enterprise personally owned devices with a work profile \(BYOD\)
  - iOS/iPadOS
  - macOS
  - Windows


  Note


  - Android Enterprise corporate-owned devices are not supported. Team viewer works with the Company portal app. It doesn't work with the Intune app.
  - TeamViewer may not support Windows Holographic \(HoloLens\) or Windows Team \(Surface Hub\). For supportability, see [TeamViewer](https://www.teamviewer.com) \(opens TeamViewer's web site\) for any updates.

- A [TeamViewer](https://www.teamviewer.com) \(opens TeamViewer's web site\) account with the sign-in credentials. Only some TeamViewer licenses support integration with Intune. For specific TeamViewer needs, see [TeamViewer Integration Partner: Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/).

By using TeamViewer, you're allowing the TeamViewer for Intune Connector to create TeamViewer sessions, read Active Directory data, and save the TeamViewer account access token.

Note

- TeamViewer is not supported on GCC High environments.

## Configure the TeamViewer connector

To provide remote assistance to devices, configure the Intune TeamViewer connector using the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** > **Connectors and tokens** > **TeamViewer Connector**.
3. Select **Connect**, and accept the license agreement.
4. Select **Log in to TeamViewer to authorize**.
5. A web page opens to the TeamViewer site. Enter your TeamViewer license credentials, and then **Sign In**.

## Remotely administer a device

After the connector is configured, you're ready to remotely administer a device.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **All devices**.
3. From the list, select the device that you want to remotely administer > **New Remote Assistance Session**. Select the three dots \(**...**\) to see this option.
4. After Intune connects to the TeamViewer service, you'll see some information about the device. **Connect** to start the remote session.

In TeamViewer, you can complete a range of actions on the device, including taking control of the device. For full details of what you can do, see the [TeamViewer community page](https://community.teamviewer.com/) \(opens TeamViewer's web site\).

When finished, close the TeamViewer window.

## End user experience

When you start a remote session, users see a notification flag on the Company Portal app icon on their device. A notification also appears when the app opens. Users can then accept the remote assistance request.

![Use TeamViewer connector to remotely administer Android device in Microsoft Intune and Intune admin center](https://learn.microsoft.com/en-us/intune/device-management/tools/media/teamviewer-legacy/android-teamviewer.png)

Note

Windows devices that are enrolled using "userless" methods, such as Device Enrollment Manager \(DEM\) and Windows Configuration Designer \(WCD\), don't show the TeamViewer notification in the Company Portal app. In these scenarios, it's recommended to use the TeamViewer portal to generate the session.

## Next steps

[Use Remote Help with Intune](https://learn.microsoft.com/en-us/intune/remote-help/)

[See device details in Intune](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/device-details)
