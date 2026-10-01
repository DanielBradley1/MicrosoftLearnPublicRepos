<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/add-copilot-endpoints-allowlist -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Add Microsoft Copilot endpoints to your allow list

Microsoft Copilot needs internet connectivity to support its features. This article lists the domain URLs that you need to add to your allow list to ensure communications through firewalls and other security mechanisms.

Note

Applies to Microsoft Copilot version 152 or later.

## Domain URLs to allow

See the following articles:

- [Microsoft 365 endpoints](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-endpoints)
- [Unified cloud.microsoft domain for Microsoft 365 apps](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cloud-microsoft-domain)

## Update Service

The service that Microsoft Copilot uses to check for new updates.

`https://msedge.api.cdp.microsoft.com`

## Experimentation and Configuration service

`https://config.edge.skype.com`

## Download locations for Microsoft Copilot

Locations where you can download Microsoft Copilot during an initial install or when an update is available. The Update Service determines the download location.

### HTTP

- `http://msedge.f.tlu.dl.delivery.mp.microsoft.com`
- `http://msedge.f.dl.delivery.mp.microsoft.com`
- `http://msedge.b.tlu.dl.delivery.mp.microsoft.com`
- `http://msedge.b.dl.delivery.mp.microsoft.com`

### HTTPS

- `https://msedge.sf.tlu.dl.delivery.mp.microsoft.com`
- `https://msedge.sf.dl.delivery.mp.microsoft.com`
- `https://msedge.sb.tlu.dl.delivery.mp.microsoft.com`
- `https://msedge.sb.dl.delivery.mp.microsoft.com`

Tip

To simplify the allow list for download locations, use a wildcard: `*.dl.delivery.mp.microsoft.com`

## Optionally for Download Delivery Optimization

For information about delivery optimization, see [Delivery Optimization for Windows 10 updates](https://learn.microsoft.com/en-us/windows/deployment/update/waas-delivery-optimization).

- Client to Service communication: `*.do.dsp.mp.microsoft.com` \(HTTP Port 80, HTTPS Port 443\)
- Client to Client communication: TCP port 7680 should be open for inbound traffic.

## Sign in

To ensure proper profile sign-in for both Microsoft personal accounts and Entra ID \(formerly Azure AD\) enterprise accounts, you need the following endpoints:

- `https://login.live.com`
- `https://login.microsoftonline.com`
- `https://login.microsoft.com`
- `https://login.windows.net`
- `https://odc.officeapps.live.com`
- `https://graph.microsoft.com`
- `https://substrate.office.com`
- `https://privacy.microsoft.com`
- `https://cdn.odc.officeapps.live.com`
- `https://logincdn.msauth.net`

Note

This list of endpoints isn't exhaustive and might be updated over time. For the latest required endpoints, refer to the official documentation.

## Additional resources

- [Microsoft Copilot app overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-overview)
- [Microsoft Copilot requirements](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements)
- [Manage connection endpoints for Windows 10 Enterprise, version 1903](https://learn.microsoft.com/en-us/windows/privacy/manage-windows-1903-endpoints)
