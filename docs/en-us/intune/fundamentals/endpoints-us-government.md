<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/endpoints-us-government -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# US government endpoints for Microsoft Intune

This article lists the US Government, US Government Community \(GCC\) High, and Department of Defense \(DoD\) endpoints needed for proxy settings in your Intune deployments.

## Before you begin

- To manage devices behind firewalls and proxy servers, you must enable communication for Intune.

  - The proxy server must support **HTTP \(80\)** and **HTTPS \(443\)**. Intune clients use both protocols.
  - For some tasks \(like downloading software updates\), Intune requires unauthenticated proxy server access to `manage.microsoft.us`.

- You can modify proxy server settings on individual client computers. You can also use Group Policy settings to change settings for all client computers located behind a specified proxy server.
- Managed devices require configurations that let **All Users** access services through firewalls.
- The inspection of SSL traffic is not supported on `*.manage.microsoft.us` or `has.spserv.microsoft.com` endpoints.

For more information about Windows auto-enrollment and device registration for US government customers, see [Set up automatic enrollment for Windows](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-automatic-mdm).

## Ports and IP addresses list

The following table lists the service endpoints, IP addresses, and ports that the Intune client accesses.

Intune endpoints also use Azure Front Door for communicating with the Intune service. Intune specific endpoints are referenced by `AzureFrontDoor.MicrosoftSecurity` in the JSON file. For the complete list of all services that utilize Azure Front Door and instructions to use the JSON file, see [Azure Front Door IP Ranges and Service Tags](https://www.microsoft.com/download/details.aspx?id=57063).

| Endpoint | IP address |
| --- | --- |
| \*.manage.microsoft.us | 52.227.99.114  <br>20.141.108.112  <br>13.72.17.166  <br>52.126.185.115  <br>52.227.211.91  <br>23.97.10.212  <br>52.227.29.124  <br>52.247.174.16  <br>52.227.29.244  <br>52.227.208.144  <br>52.227.1.233  <br>20.141.104.221  <br>52.247.134.218  <br>20.141.78.227  <br>13.77.236.201  <br>62.10.86.128/25  <br>62.10.87.128/25  <br>20.159.110.0/25  <br>20.159.111.0/25  <br>  <br>Azure Front Door:  <br>51.54.53.136/29  <br>51.54.114.160/29  <br>62.11.173.176/29 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239  <br>13.72.55.179 |

## US Government customer designated endpoints

- Azure portal: `https://portal.azure.us/`
- Microsoft 365: `https://portal.office365.us/`
- Intune Company Portal: `https://portal.manage.microsoft.us/`
- Microsoft Intune admin center: `https://intune.microsoft.us/`

## Network requirements for PowerShell scripts and Win32 apps

If you're using Intune to deploy PowerShell scripts or Win32 apps, you also need to grant access to endpoints in which your tenant currently resides.

| Azure Scale Unit \(ASU\) | Storage name | CDN |
| --- | --- | --- |
| FXPASU01 | sovereignprodimedatapri  <br>sovereignprodimedatasec  <br>sovereignprodimedatahotfix | imeswdsc-afd-pri.manage.microsoft.com  <br>imeswdsc-afd-sec.manage.microsoft.com  <br>imeswdsc-afd-hotfix.manage.microsoft.com |

For diagnostic data used to monitor the health of the client side components:

- `*.events.data.microsoft.com`

## Microsoft Defender for Endpoint

For more information about configuring Defender for Endpoint connectivity, see [Connectivity Requirements](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/security-settings-management#connectivity-requirements).

To support Defender for Endpoint security settings management, allow the following hostnames through your firewall.

For communication between clients and the cloud service:

- `*.dm.microsoft.us` - The use of a wildcard supports the cloud-service endpoints that are used for enrollment, check-in, and reporting, and which can change as the service scales.

  Important

  SSL Inspection is not supported on endpoints required for Microsoft Defender for Endpoint.

## Microsoft Intune Endpoint Privilege Management

To support Endpoint Privilege Management, allow the following hostnames through your firewall.

For communication between clients and the cloud service:

- `*.dm.microsoft.us` - The use of a wildcard supports the cloud-service endpoints that are used for enrollment, check-in, and reporting, and which can change as the service scales.

  Important

  SSL Inspection isn't supported on endpoints required for Endpoint Privilege Management.

For more information, see the [Overview of Endpoint Privilege Management](https://learn.microsoft.com/en-us/intune/epm/overview).

## Partner service endpoints that Intune depends on

- Azure AD Sync service: `https://syncservice.gov.us.microsoftonline.com/DirectoryService.svc`
- Evo STS: `https://login.microsoftonline.us`
- Directory Proxy: `https://directoryproxy.microsoftazure.us/DirectoryProxy.svc`
- Azure AD Graph: `https://directory.microsoftazure.us` and `https://graph.microsoftazure.us`
- MS Graph: `https://graph.microsoft.us`
- ADRS: `https://enterpriseregistration.microsoftonline.us`
- Experimentation and Configuration Service \(ECS\): `*.ecs.gov.teams.microsoft.us`

## Windows Push Notification Services

On Intune-managed devices managed by using Mobile Device Management \(MDM\), Windows Push Notification Services \(WNS\) is required for device actions and other immediate activities. For more information, see [Enterprise Firewall and Proxy Configurations to Support WNS Traffic](https://learn.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## Apple dependencies

For information about Apple specific endpoints, see the following resources:

- [Use Apple products on enterprise networks](https://support.apple.com/HT210060)
- [TCP and UDP ports used by Apple software products](https://support.apple.com/HT202944)
- [About macOS, iOS/iPadOS, and iTunes server host connections and iTunes background processes](https://support.apple.com/HT201999)
- [If your macOS and iOS/iPadOS clients aren't getting Apple push notifications](https://support.apple.com/HT203609)

## Next steps

[Network endpoints for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/endpoints)
