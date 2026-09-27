<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/endpoints-china -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# China endpoints for Microsoft Intune

This page lists the China endpoints that are needed for proxy settings in your Intune deployments.

To manage devices behind firewalls and proxy servers, you must enable communication for Intune.

- The proxy server must support both **HTTP \(80\)** and **HTTPS \(443\)** because Intune clients use both protocols
- For some tasks \(like downloading software updates\), Intune requires unauthenticated proxy server access to manage.microsoft.com

You can modify proxy server settings on individual client computers. You can also use Group Policy settings to change settings for all client computers located behind a specified proxy server.

Managed devices require configurations that let **All Users** access services through firewalls.

For more information about Windows auto-enrollment and device registration for U.S. customers, see [Windows auto enrollment and device registration](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/create-cname-autodiscovery#windows-auto-enrollment-and-device-registration).

Note

Intune endpoints also use *Azure Front Door* for communicating with the Intune service. The IP ranges for Intune are added to the following table. Intune specific endpoints are referenced in the JSON file by the name `AzureFrontDoor.Frontend`. Refer to the Azure Front Door and Service Tags documentation for the complete list of all services that utilize Azure Front Door and instructions for using the JSON file. [Azure Front Door IP Ranges and Service Tags](https://www.microsoft.com/download/details.aspx?id=57062)

The following tables list the ports and services that the Intune client accesses:

| **Endpoint** | **IP address** |
| --- | --- |
| \*.manage.microsoftonline.cn | 40.73.38.143  <br>139.217.97.81  <br>52.130.80.24  <br>40.73.41.162  <br>40.73.58.153  <br>139.217.95.85  <br>143.64.196.128/25  <br>40.162.2.128/25  <br>139.219.250.128/25  <br>163.228.221.128/25  <br>  <br>Azure Front Door Endpoints:  <br>52.131.21.32/29  <br>52.131.149.32/29  <br>143.64.194.48/29  <br>159.27.145.240/29  <br>159.27.248.128/29  <br>2159.27.255.224/29  <br>163.228.60.104/29  <br>163.228.102.88/29  <br>163.228.195.128/29  <br>163.228.218.208/29  <br>2404:7940:1::5e0/123  <br>2404:7940:101::5e0/123  <br>2404:7940:201::5e0/123  <br>2404:7940:301::5e0/123  <br>2406:e500:2402:1::480/123  <br>2406:e500:2602:1::480/123  <br> |

## Intune customer designated endpoints in China

- Azure portal: `https:\//portal.azure.cn/`
- Microsoft 365: `https:\//portal.partner.microsoftonline.cn/`
- Intune Company Portal: `https:\//portal.manage.microsoftonline.cn/`
- Microsoft Intune admin center: `https:\//intune.microsoftonline.cn/`

## Network requirements for PowerShell scripts and Win32 apps

If you're using Intune to deploy PowerShell scripts or Win32 apps, you also need to grant access to endpoints in which your tenant currently resides.

| Azure Scale Unit \(ASU\) | Storage name | CDN |
| --- | --- | --- |
| CNPASU01 | sovereignprodimedatapri  <br>sovereignprodimedatasec  <br>sovereignprodimedatahotfix | imeswdsc-afd-pri.manage.microsoft.com  <br>imeswdsc-afd-sec.manage.microsoft.com  <br>imeswdsc-afd-hotfix.manage.microsoft.com |

## Network requirements for macOS app and script deployments

If you're using Intune to deploy apps or scripts on macOS, you also need to grant access to endpoints in which your tenant currently resides.

| Azure Scale Unit \(ASU\) | Storage Name | CDN |
| --- | --- | --- |
| CNPASU01 | macsidecarap  <br>macsidecarprodap | macsidecarap.manage.microsoft.com |

## Partner service endpoints

Intune operated by 21Vianet depends on the following partner service endpoints:

- Azure AD Sync service: `https://syncservice.partner.microsoftonline.cn/DirectoryService.svc`
- Evo STS: `https://login.chinacloudapi.cn/`
- Azure AD `Graph: https://graph.chinacloudapi.us`
- MS Graph: `https://microsoftgraph.chinacloudapi.cn`
- ADRS: `https://enterpriseregistration.partner.microsoftonline.cn`
- Experimentation and Configuration Service \(ECS\): `https://mooncake.ecs.office.com`

## Windows Push Notification Services

On Intune-managed devices managed by using Mobile Device Management \(MDM\), Windows Push Notification Services \(WNS\) is required for device actions and other immediate activities. For more information, see [Enterprise Firewall and Proxy Configurations to Support WNS Traffic](https://learn.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## Apple dependencies

For information about Apple specific endpoints, see the following resources:

- [Use Apple products on enterprise networks](https://support.apple.com/HT210060)
- [TCP and UDP ports used by Apple software products](https://support.apple.com/HT202944)
- [About macOS, iOS/iPadOS, and iTunes server host connections and iTunes background processes](https://support.apple.com/HT201999)
- [If your macOS and iOS/iPadOS clients aren't getting Apple push notifications](https://support.apple.com/HT203609)

## Related articles

[Learn more about Intune operated by 21Vianet in China](https://learn.microsoft.com/en-us/intune/fundamentals/china)
