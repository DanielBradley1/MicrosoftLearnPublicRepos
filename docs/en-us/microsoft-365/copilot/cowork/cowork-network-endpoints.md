<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-network-endpoints -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Cowork network endpoints

This article lists the network endpoints, application identities, and proxy configuration requirements that your organization needs to allow for Copilot Cowork to function correctly. Use this information when preparing firewall allow lists, proxy exemptions, or Conditional Access policy reviews.

Where possible, bypass SSL/TLS decryption, traffic inspection devices, and other network intermediaries for Microsoft 365 traffic. Network devices that decrypt, inspect, and re-encrypt Microsoft 365 connections can impact availability, performance, interoperability, and supportability. For Cowork traffic to \*.gateway.prod.island.powerapps.com:443, SSL/TLS inspection isn't supported and might interrupt long-lived SSE connections. This condition can result in message delivery failures, retries, or frozen tasks.

Learn more in the following articles:

- [Assess bypassing proxies, traffic inspection devices, and duplicate security technologies](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)
- [Understanding implications when using network intermediation to decrypt or manipulate Microsoft 365 traffic at the network layer](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-intermediation)

## UX entry points

Users access Cowork through Microsoft Copilot Chat. The following URLs must be reachable from user devices:

| Component | URL |
| --- | --- |
| Microsoft Copilot Chat | `https:⁠//copilot.cloud.microsoft/chat` |
| Cowork agent | `https:⁠//copilot.cloud.microsoft/chat/agent/&lt;agent-id&gt;.weave` |

## Cowork service endpoints

All Cowork service traffic flows through a single host pattern. A routing service returns the regional runtime URL for the authenticated user, and subsequent traffic flows directly to that runtime endpoint.

| Purpose | Host pattern | Port |
| --- | --- | --- |
| Routing service \(first hop\) | `*.gateway.prod.island.powerapps.com` | 443 |
| Regional runtime \(returned by routing service\) | `*.gateway.prod.island.powerapps.com` | 443 |

**Recommended allowlist entry:** `*.gateway.prod.island.powerapps.com:443`

A single wildcard covers both routing and runtime in all regions. Don't pin to specific regional subdomains, because routing decisions are made dynamically per user and might change over time.

The cluster identifier assigned to each tenant might also change, so use the wildcard pattern rather than hard-coding a specific cluster.

Note

- These endpoints are part of the Power Apps infrastructure. If your organization doesn't already use Power Apps, these endpoints might not be on your existing allow list.
- You can find the complete Power Apps endpoint list in [Power Apps required endpoints \(public cloud\)](https://learn.microsoft.com/en-us/power-apps/limits-and-config).

## IP address ranges for firewall configuration

Allow lists based on URLs are recommended. If your firewall or proxy requires IP address ranges instead, allow the CIDR blocks published for the **PowerPlatformInfra** service tag, which covers the Cowork service endpoints that run on Power Platform infrastructure.

To get the current ranges, download [Azure IP Ranges and Service Tags - Public Cloud](https://www.microsoft.com/download/details.aspx?id=56519) and find the `PowerPlatformInfra` service tag in the JSON file. The `addressPrefixes` property lists the IPv4 and IPv6 CIDR blocks. If your firewall supports Azure service tags directly, reference `PowerPlatformInfra` instead of individual ranges. Learn more in [Virtual network service tags](https://learn.microsoft.com/en-us/azure/virtual-network/service-tags-overview).

Important

These IP ranges change over time. The published list is updated weekly, and new ranges appear in the file at least one week before they're used. Download the file on a recurring basis so your allow list stays current.

## Standard Microsoft 365 dependencies

Cowork relies on standard Microsoft 365 services that are typically already permitted for any tenant using Microsoft 365. Confirm that the following destinations are allowed:

| Destination | Port | Purpose |
| --- | --- | --- |
| `copilot.cloud.microsoft` | 443 | UX entry point \(Copilot Chat host\) |
| `login.microsoftonline.com` | 443 | Microsoft Entra ID authentication and key validation |
| `graph.microsoft.com` | 443 | Microsoft 365 services \(mail, files, calendar, people\) |

## Microsoft Entra ID application for Conditional Access

Cowork uses a single Microsoft application as the token audience for all service requests. Your Conditional Access policies must permit this application ID:

| Application | Client ID | Purpose |
| --- | --- | --- |
| Weave / M365 Host App | 6ab48b67-cd74-4ad4-81af-5932984589be | Token audience for all Cowork service requests |

Microsoft Entra ID administrators should confirm:

- Conditional Access policies don't block the previously listed application.
- Workload identity credentials \(service principals\) can acquire tokens in the tenant for this application.
- On-Behalf-Of consent is granted for the required Microsoft 365 service scopes.

## Long-lived connection requirements

Cowork uses persistent streaming connections for real-time updates. Corporate proxies and gateways must not terminate these connections prematurely.

| Endpoint path | Required proxy timeout |
| --- | --- |
| /v1/subscribe | No timeout, or 30 minutes minimum |
| /v1/mru/subscribe | No timeout, or 30 minutes minimum |

Important

Proxies that enforce an absolute-lifetime timeout \(rather than an idle timeout\) terminate these streams even when traffic is flowing. The server sends periodic keep-alive signals, but absolute-lifetime limits still cause disconnects. Exempt *\*.gateway.prod.island.powerapps.com* from absolute-lifetime timeout rules, or set the limit to 30 minutes minimum.

## Full endpoint allow list

The following table summarizes all destinations that must be reachable for Cowork to function:

| Destination | Port | Purpose |
| --- | --- | --- |
| `*.gateway.prod.island.powerapps.com` | 443 | Routing and runtime service endpoints |
| `copilot.cloud.microsoft` | 443 | UX entry point \(Copilot Chat\) |
| `login.microsoftonline.com` | 443 | Microsoft Entra ID authentication and key validation |
| `graph.microsoft.com` | 443 | Microsoft 365 services \(mail, files, calendar, people\) |

## Minimum requirements checklist

Use the following checklist to verify your environment is ready for Cowork:

- **Microsoft 365 Copilot license** assigned to each user.
- **Conditional Access**: Allow application ID `6ab48b67-cd74-4ad4-81af-5932984589be` \(Weave / M365 Host App\).
- **Proxy and firewall allowlist**: Add `*.gateway.prod.island.powerapps.com:443` with no absolute-lifetime timeout on streaming connections \(or set the limit to 30 minutes minimum\).
- **Standard Microsoft 365 URLs**: Confirm that `copilot.cloud.microsoft`, `login.microsoftonline.com`, and `graph.microsoft.com` are allowed. These are typically already permitted for general Microsoft 365 usage.

## Related content

- [Power Apps required endpoints \(public cloud\)](https://learn.microsoft.com/en-us/power-apps/limits-and-config)
- [Power Apps required endpoints \(government cloud\)](https://learn.microsoft.com/en-us/power-platform/admin/powerapps-us-government)
- [Azure IP Ranges and Service Tags - Public Cloud](https://www.microsoft.com/download/details.aspx?id=56519)
