<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-windows-8-1 -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Add VPN settings on Windows 8.1 devices in Microsoft Intune

Important

On October 22, 2022, Microsoft Intune ended support for devices running Windows 8.1. Technical assistance and automatic updates on these devices aren't available.

This article shows you the Intune settings you can use to configure VPN connections on devices running Windows 8.1.

Depending on the settings you choose, not all values in the following list are configurable.

## Before you begin

- [Create a Windows 8.1 VPN device configuration profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-vpn).
- Some Microsoft 365 services, such as Outlook, might not perform well using third party or partner VPNs. If you're using a third party or partner VPN, and experience a latency or performance issue, then remove the VPN.

  If removing the VPN resolves the behavior, then you can:

  - Work with the third party or partner VPN for possible resolutions. Microsoft doesn't provide technical support for third party or partner VPNs.
  - Don't use a VPN with Outlook traffic.
  - If you need to use a VPN, then use a split-tunnel VPN. And, allow the Outlook traffic to bypass the VPN.


  For more information, go to:


  - [Overview: VPN split tunneling for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel)
  - [Using third-party network devices or solutions with Microsoft 365](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365-apps/office-suite-issues/office-365-third-party-network-devices)
  - [Microsoft 365 network connectivity principles](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)

## Base VPN settings

- **Connection name**: Enter a name for this connection. Users see this name when they browse their device for the list of available VPN connections. For example, enter `Contoso VPN`.
- **Servers**: Add one or more VPN servers that devices connect to. When you add a server, you enter the following information:

  - **Description**: Enter a descriptive name for the server, like **Contoso VPN server**.
  - **IP address or FQDN**: Enter the IP address or fully qualified domain name \(FQDN\) of the VPN server that devices connect to. For example, enter `192.168.1.1` or `vpn.contoso.com`.
  - **Default server**: **True** sets this server as the default server that devices use to establish the connection. Set only one server as the default.
  - **Import**: Browse to a comma-separated file with the list of servers in the format: description, IP address or FQDN, Default server. Choose **OK** to import these servers into the **Servers** list.
  - **Export**: Exports the list of servers to a comma-separated-values \(csv\) file.

- **Connection type**: Select the VPN connection type. Your options:

  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**

- **Login group or domain** \(SonicWall Mobile Connect only\): Enter the name of the login group or domain you want to connect to.
- **Custom XML**: Enter any custom XML commands that configure the VPN connection.

  **Pulse Secure example**:

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```


  **CheckPoint Mobile VPN example**:


  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```


  **SonicWall Mobile Connect example**:


  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```


  **F5 Edge Client example**:


  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```


  For more information on writing custom XML commands, go to the manufacturer's VPN documentation.

- **Split tunneling**: **Enable** lets devices decide which connection to use depending on the traffic. For example, a user in a hotel uses the VPN connection to access work files, but use the hotel's standard network for regular web browsing.

  If you want all traffic to use the VPN tunnel when the VPN connection is active, then set to **Disable**.

## Proxy

- **Automatic configuration script**: Use a file to configure the proxy server. Enter the proxy server URL that includes the configuration file. For example, enter `http://proxy.contoso.com/pac`.
- **Address**: Enter the IP address or fully qualified host name of the proxy server. For example, enter `10.0.0.3` or `vpn.contoso.com`.
- **Port number**: Enter the port number associated with the proxy server. For example, enter `8080`.
- **Automatically detect proxy settings**: If your VPN server requires a proxy server for the connection, choose if you want devices to automatically detect the connection settings. Your options:

  - **Not configured** \(default\): Intune doesn't change or update this setting.
  - **Enable**: Automatically detects the connection settings.
  - **Disable**: Doesn't automatically detect the connection settings.

- **Bypass proxy for local addresses**: Choose to use the proxy server for local addresses. Your options:

  - **Not configured** \(default\): Intune doesn't change or update this setting.
  - **Enable**: Don't use a proxy server for local addresses.
  - **Disable**: Use a proxy server for local addresses.

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile), and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- Configure VPN settings on [Android](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android), [Android Enterprise](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android-enterprise), [macOS](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-apple), and [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-windows) devices.
