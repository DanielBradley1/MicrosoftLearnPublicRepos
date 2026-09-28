<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-requirements?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Requirements for Copilot Pages and Copilot Notebooks

Copilot Pages and Copilot Notebooks are stored in a user-owned SharePoint Embedded container that's also used by Loop My workspace. Across the SharePoint admin center, PowerShell, and Purview audit data, this container's application name is always `Loop` — even when it only stores Copilot Pages or Copilot Notebooks. There's no separate Copilot Pages or Copilot Notebooks application filter.

## At a glance

| Requirement | Details |
| --- | --- |
| **Copilot Pages license** | OneDrive license \(requires OneDrive site\) |
| **Copilot Notebooks license** | Microsoft Copilot license |
| **Network** | Allow connections per [Office 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| **Real-time collaboration** | Allow WebSocket traffic to `*.svc.ms` and `*.office.com` |
| **Full features** | Exchange Online mailbox required for @mentions |

## Overview

Copilot Pages create `.page` files and Copilot Notebooks create `.pod` files, both stored in the same user-owned SharePoint Embedded container used by Loop My workspace. Storage counts against your organization's SharePoint quota. For details, see [storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide). To control creation, see [admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide).

## Network requirements

### URLs and IP address ranges

Verify that required network connections are allowed. Copilot Pages and Copilot Notebooks rely on core Microsoft 365 and SharePoint infrastructure. Configure your firewall or proxy settings according to [Office 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges).

### WebSocket connections

Allow WebSocket traffic to `*.svc.ms` and `*.office.com` endpoints. WebSocket connections enable real-time collaboration features including live editing, presence indicators, and shared cursors.

## License requirements

### Copilot Pages

Users need a OneDrive license and an active OneDrive site. If a OneDrive site exists and the license is later removed, Copilot Pages continue to work.

### Copilot Notebooks

Users need the [Microsoft Copilot or Copilot Chat license](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing).

## Exchange Online requirement

For full functionality including @mentions, users need an Exchange Online mailbox. Users with Exchange On-Premises mailboxes have limited capabilities.

## Relationship to Loop components

Copilot Pages and Copilot Notebooks are independent of Loop. You can enable or disable them separately. They do share a single user-owned SharePoint Embedded container with Loop My workspace; for the full explanation of that shared container, including how to prevent it from being created, see [storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide).

To share Copilot Pages as interactive components in Teams, Outlook, Whiteboard, OneNote, or the Loop app, Loop components must be enabled. Without Loop components enabled in the Microsoft 365 ecosystem, Copilot Pages are only interactive within the Microsoft Copilot app and supported chat experiences. For details on enabling Loop components, see [Loop admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide).

## Related articles

- [Admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide)
- [Storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide)
- [Permissions](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-permission?view=o365-worldwide)
- [Summary of compliance capabilities](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-compliance-summary?view=o365-worldwide)
- [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
