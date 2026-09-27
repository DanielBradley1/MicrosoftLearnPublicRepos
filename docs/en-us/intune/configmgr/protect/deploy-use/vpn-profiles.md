<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/vpn-profiles -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# VPN profiles in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/resource-access-deprecation-faq).

To deploy VPN settings to users in your organization, use VPN profiles in Configuration Manager. By deploying these settings, you minimize the end-user effort required to connect to resources on the company network.

For example, you want to configure all Windows 10 devices with the settings required to connect to a file share on the internal network. Create a VPN profile with the settings necessary to connect to the internal network. Then deploy this profile to all users that have devices running Windows 10. These users see the VPN connection in the list of available networks and can connect with little effort.

When you create a VPN profile, you can include a wide range of security settings. These settings include certificates for server validation and client authentication that you provision with Configuration Manager certificate profiles. For more information, see [Certificate profiles](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/introduction-to-certificate-profiles).

Note

Configuration Manager doesn't enable this optional feature by default. You must enable this feature before using it. For more information, see [Enable optional features from updates](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/optional-features).

## Supported platforms

The following table describes the VPN profiles you can configure for various device platforms.

| Connection type | Windows 8.1 | Windows RT | Windows RT 8.1 | Windows 10 |
| --- | --- | --- | --- | --- |
| **Pulse Secure** | Yes | No | Yes | Yes |
| **F5 Edge Client** | Yes | No | Yes | Yes |
| **Dell SonicWALL Mobile Connect** | Yes | No | Yes | Yes |
| **Check Point Mobile VPN** | Yes | No | Yes | Yes |
| **Microsoft SSL \(SSTP\)** | Yes | Yes | Yes | No |
| **Microsoft Automatic** | Yes | Yes | Yes | No |
| **IKEv2** | Yes | Yes | Yes | No |
| **PPTP** | Yes | Yes | Yes | No |
| **L2TP** | Yes | Yes | Yes | No |

## Next step

[How to create VPN profiles](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/create-vpn-profiles)

## See also

- [Prerequisites for VPN profiles](https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/prerequisites-for-wifi-vpn-profiles)
- [Security and privacy for VPN profiles](https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/security-and-privacy-for-wifi-vpn-profiles)
