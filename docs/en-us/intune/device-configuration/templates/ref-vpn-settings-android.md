<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Android device administrator settings that configure VPN in Intune

This article describes the different VPN connection settings you can control on Android devices. As part of your mobile device management \(MDM\) solution, use these settings to create a VPN connection, choose how the VPN authenticates, select a VPN server type, and more.

This feature applies to:

- Android device administrator \(DA\)

As an Intune administrator, you can create and assign VPN settings to Android devices. To learn more about VPN profiles in Intune, go to [VPN profiles](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-vpn).

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Before you begin

- Create an [Android device administrator VPN device configuration profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-vpn).
- Some Microsoft 365 services, such as Outlook, might not perform well using third party or partner VPNs. If you're using a third party or partner VPN, and experience a latency or performance issue, then remove the VPN.

  If removing the VPN resolves the behavior, then you can:

  - Work with the third party or partner VPN for possible resolutions. Microsoft doesn't provide technical support for third party or partner VPNs.
  - Don't use a VPN with Outlook traffic.
  - If you need to use a VPN, then use a split-tunnel VPN. And, allow the Outlook traffic to bypass the VPN.


  For more information, go to:


  - [Overview: VPN split tunneling for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel)
  - [Using third-party network devices or solutions with Microsoft 365](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365-apps/office-suite-issues/office-365-third-party-network-devices)
  - [Microsoft 365 network connectivity principles](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)

## Base VPN

- **Connection name**: Enter a name for this connection. End users see this name when they browse their device for the available VPN connections. For example, enter `Contoso VPN`.
- **VPN server address**: Enter the IP address or fully qualified domain name \(FQDN\) of the VPN server that devices connect. For example, enter `192.168.1.1` or `vpn.contoso.com`.
- **Authentication method**: Select how devices authenticate to the VPN server. Your options:

  - **Certificates**: Select an existing SCEP or PKCS certificate profile to authenticate the connection. [Configure certificates](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview) lists the steps to create a certificate profile.
  - **Username and password**: When users sign in to the VPN server, they're prompted to enter their user name and password.

    For more information, go to [Use derived credentials in Intune](https://learn.microsoft.com/en-us/intune/device-security/certificates/derived-credentials).

- **Connection type**: Select the VPN connection type. Your options:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **Fingerprint** \(Check Point Capsule VPN only\): Enter the fingerprint string given to you by the VPN vendor, like `Contoso Fingerprint Code`. This fingerprint verifies that the VPN server can be trusted.

  When authenticating, a fingerprint is sent to the client so the client knows to trust any server that has the same fingerprint. If the device doesn't have the fingerprint, it prompts the user to trust the VPN server while showing the fingerprint. The user manually verifies the fingerprint, and chooses to trust to connect.

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- Create VPN profiles for [Android Enterprise](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android-enterprise), [iOS/iPadOS and macOS](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-apple), and [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-windows).
