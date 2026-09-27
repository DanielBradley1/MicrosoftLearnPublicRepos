<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android-enterprise -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Android Enterprise device settings to configure VPN in Intune

This article describes the different VPN connection settings you can control on Android Enterprise devices. As part of your mobile device management \(MDM\) solution, use these settings to create a VPN connection, choose how the VPN authenticates, select a VPN server type, and more.

This feature applies to:

- Android Enterprise personally owned devices with a work profile \(BYOD\)
- Android Enterprise corporate-owned work profile \(COPE\)
- Android Enterprise corporate owned fully managed \(COBO\)
- Android Enterprise corporate owned dedicated devices \(COSU\)

As an Intune administrator, you can create and assign VPN settings to Android Enterprise devices. To learn more about VPN profiles in Intune, see [VPN profiles](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-vpn).

Note

To configure always-on VPN, you need to:

1. Create a VPN profile with your connection info, as described in this article.
2. Create an [Android Enterprise device restrictions](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android-enterprise) > **Corporate-owned** > **Connectivity** profile with the Always-on VPN setting configured.
3. Assign both profiles to your groups.

## Before you begin

- Create an [Android Enterprise VPN device configuration profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-vpn):

  - Fully managed, dedicated, and corporate-owned work profile
  - Personally owned work profile

- Some Microsoft 365 services, such as Outlook, might not perform well using third party or partner VPNs. If you're using a third party or partner VPN, and experience a latency or performance issue, then remove the VPN.

  If removing the VPN resolves the behavior, then you can:

  - Work with the third party or partner VPN for possible resolutions. Microsoft doesn't provide technical support for third party or partner VPNs.
  - Don't use a VPN with Outlook traffic.
  - If you need to use a VPN, then use a split-tunnel VPN. And, allow the Outlook traffic to bypass the VPN.


  For more information, go to:


  - [Overview: VPN split tunneling for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel)
  - [Using third-party network devices or solutions with Microsoft 365](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365-apps/office-suite-issues/office-365-third-party-network-devices)
  - [Microsoft 365 network connectivity principles](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)

- If you need these devices to access on-premises resources using modern authentication and Conditional Access, then you can use the [Microsoft Tunnel](https://learn.microsoft.com/en-us/intune/device-security/microsoft-tunnel/overview), which supports split tunneling.

## Fully Managed, Dedicated, and Corporate-Owned Work Profile

- **Connection type**: Select the VPN connection type. Your options:

  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Microsoft Tunnel** \(Not supported on Android Enterprise dedicated devices.\)

The available settings depend on the VPN client you choose. Some settings are only available for specific VPN clients.

### Base VPN \(fully managed, dedicated, and corporate-owned work profile\)

- **Connection name**: Enter a name for this connection. End users see this name when they browse their device for the available VPN connections. For example, enter `Contoso VPN`.
- **VPN server address or FQDN**: Enter the IP address or fully qualified domain name \(FQDN\) of the VPN server that devices connect. For example, enter `192.168.1.1` or `vpn.contoso.com`.
- **Authentication method**: Choose how devices authenticate to the VPN server. Your options:

  - **Certificates**: Select an existing SCEP or PKCS certificate profile that authenticates the connection. [Configure certificates](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview) lists the steps to create a certificate profile.
  - **Username and password**: When end users sign in to the VPN server, users are prompted to enter their user name and password.
  - **Derived credential**: Use a certificate that is derived from a user's smart card. If no derived credential issuer is configured, Intune prompts you to add one.

    For more information, see [Use derived credentials in Intune](https://learn.microsoft.com/en-us/intune/device-security/certificates/derived-credentials).

- **Enter key and value pairs for the NetMotion Mobility VPN attributes**: Add or import **Keys** and **Values** that customize your VPN connection. These values are typically supplied by your VPN provider.
- **Microsoft Tunnel site** \(Microsoft Tunnel only\): Select an existing site. The VPN client connects to the public IP address or FQDN of this site.

  For more information, see [Microsoft Tunnel for Intune](https://learn.microsoft.com/en-us/intune/device-security/microsoft-tunnel/overview).

### Per-app VPN \(fully managed, dedicated, and corporate-owned work profile\)

- **Add**: Select managed apps from the list. When users start the apps you add, traffic automatically routes through the VPN connection.

For more information, see [Use a VPN and per-app VPN policy on Android Enterprise devices](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-vpn-android).

### Always-on VPN \(fully managed, dedicated, and corporate-owned work profile\)

- **Always-on VPN**: **Enable** turns on always-on VPN so VPN clients automatically connect and reconnect to the VPN when possible. When set to **Not configured**, Intune doesn't change or update this setting. By default, always-on VPN might be disabled for all VPN clients.

  Only one VPN client can be configured for always-on VPN on a device. Be sure to have no more than one always-on VPN policy deployed to a single device.

### Proxy \(fully managed, dedicated, and corporate-owned work profile\)

- **Automatic configuration script**: Use a file to configure the proxy server. Enter the proxy server URL that includes the configuration file. For example, enter `http://proxy.contoso.com/pac`.
- **Address**: Enter the IP address or fully qualified host name of the proxy server. For example, enter `10.0.0.3` or `vpn.contoso.com`.
- **Port number**: Enter the port number associated with the proxy server. For example, enter `8080`.

## Personally owned work profile

- **Connection type**: Select the VPN connection type. Your options:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**

    Note

    With Cisco AnyConnect in the personally owned work profile, there may be some extra steps for end users to complete the VPN connection. For more information, go to [VPN profiles - What successful VPN profiles look like](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/device-configuration/troubleshoot-vpn-profiles?tabs=android#what-successful-vpn-profiles-look-like).
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **NetMotion Mobility**
  - **Microsoft Tunnel**

The available settings depend on the VPN client you choose. Some settings are only available for specific VPN clients.

### Base VPN \(personally owned work profile\)

- **Connection name**: Enter a name for this connection. End users see this name when they browse their device for the available VPN connections. For example, enter `Contoso VPN`.
- **VPN server address**: Enter the IP address or fully qualified domain name \(FQDN\) of the VPN server that devices connect. For example, enter `192.168.1.1` or `vpn.contoso.com`.
- **Authentication method**: Choose how devices authenticate to the VPN server. Your options:

  - **Certificates**: Select an existing SCEP or PKCS certificate profile that authenticates the connection. [Configure certificates](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview) lists the steps to create a certificate profile.
  - **Username and password**: When end users sign in to the VPN server, users are prompted to enter their user name and password.
  - **Derived credential**: Use a certificate that is derived from a user's smart card. If no derived credential issuer is configured, Intune prompts you to add one.

    For more information, see [Use derived credentials in Intune](https://learn.microsoft.com/en-us/intune/device-security/certificates/derived-credentials).

- **Fingerprint** \(Check Point Capsule VPN only\): Enter the fingerprint string given to you by the VPN vendor, such as `Contoso Fingerprint Code`. This fingerprint verifies that the VPN server can be trusted.

  When authenticating, a fingerprint is sent to the client so the client knows to trust any server that has the same fingerprint. If the device doesn't have the fingerprint, it prompts the user to trust the VPN server while showing the fingerprint. The user manually verifies the fingerprint, and chooses to trust to connect.
- **Enter key and value pairs for the NetMotion Mobility VPN attributes**: Add or import **Keys** and **Values** that customize your VPN connection. These values are typically supplied by your VPN provider.
- **Microsoft Tunnel site** \(Microsoft Tunnel only\): Select an existing site. The VPN client connects to the public IP address or FQDN of this site.

  For more information, see [Microsoft Tunnel for Intune](https://learn.microsoft.com/en-us/intune/device-security/microsoft-tunnel/overview).

### Per-app VPN \(personally owned work profile\)

- **Add**: Select managed apps from the list. When users start the apps you add, traffic automatically routes through the VPN connection.

For more information, see [Use a VPN and per-app VPN policy on Android Enterprise devices](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-vpn-android).

### Always-on VPN \(personally owned work profile\)

- **Always-on VPN**: **Enable** turns on always-on VPN so VPN clients automatically connect and reconnect to the VPN when possible. When set to **Not configured**, Intune doesn't change or update this setting. By default, always-on VPN might be disabled for all VPN clients.

  Only one VPN client can be configured for always-on VPN on a device. Be sure to have no more than one always-on VPN policy deployed to a single device.

### Proxy \(personally owned work profile\)

- **Automatic configuration script**: Use a file to configure the proxy server. Enter the proxy server URL that includes the configuration file. For example, enter `http://proxy.contoso.com/pac`.
- **Address**: Enter the IP address or fully qualified host name of the proxy server. For example, enter `10.0.0.3` or `vpn.contoso.com`.
- **Port number**: Enter the port number associated with the proxy server. For example, enter `8080`.

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- Create VPN profiles for [Android device administrator](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android), [iOS/iPadOS and macOS](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-apple), and [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-windows).
- Learn how to [Troubleshoot VPN profile issues in Microsoft Intune](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/device-configuration/troubleshoot-vpn-profiles).
