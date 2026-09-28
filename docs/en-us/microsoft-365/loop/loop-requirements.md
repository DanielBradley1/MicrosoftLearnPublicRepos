<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/loop-requirements?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Requirements for Loop components and Loop workspaces

## At a glance

| Requirement | Details |
| --- | --- |
| **Loop components license** | OneDrive or SharePoint license |
| **Loop workspaces license** | Loop with workspaces service plan \([see eligible licenses](https://support.microsoft.com/office/loop-access-via-microsoft-365-subscriptions-92915461-4b14-49a4-9cd4-d1c259292afa)\) |
| **Network** | Allow connections per [Office 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| **Real-time collaboration** | Allow WebSocket traffic to `*.svc.ms` and `*.office.com` |
| **Full features** | Exchange Online mailbox required for @mentions and workspace sharing |
| **Cloud environment availability** | Loop availability varies by environment and app integration \([see matrix](#cloud-environment-availability)\) |

## Overview

Loop components create `.loop` files \(earlier releases created `.fluid` files\), stored in OneDrive, SharePoint, or SharePoint Embedded. Storage counts against your organization's SharePoint quota. For details, see [storage](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide). To control creation, see [admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide).

## Network requirements

### URLs and IP address ranges

Verify that required network connections are allowed. Loop relies on core Microsoft 365 and SharePoint infrastructure. Configure your firewall or proxy settings according to [Office 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges).

### WebSocket connections

Allow WebSocket traffic to `*.svc.ms` and `*.office.com` endpoints. WebSocket connections enable real-time collaboration features including live editing, presence indicators, and shared cursors.

## License requirements

Users need a OneDrive or SharePoint license.

## Exchange Online requirement

For full functionality including @mentions and workspace sharing, users need an Exchange Online mailbox. Users with Exchange On-Premises mailboxes have limited capabilities.

## Cloud environment availability

Loop availability varies by app integration and cloud environment. For public cloud environment naming and definitions, see [Cross-cloud collaboration with Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-cloud-collaboration?view=o365-worldwide).

| Loop experience / app integration | Commercial cloud | US government cloud environments \(GCC, GCC High, DoD\) | Sovereign cloud: Bleu | Sovereign cloud: Delos | Air-gapped cloud environments |
| --- | --- | --- | --- | --- | --- |
| Loop workspaces | ✅ Available | ❌ Not available | ❌ Not available | ❌ Not available | ❌ Not available |
| Loop components in Teams \(chat, channels, chat notes, meeting notes\) | ✅ Available | ✅ Available | ✅ Available | ❌ Not available | ❌ Not available |
| Loop components in Outlook and Teams New Calendar | ✅ Available | ❌ Not available | ✅ Available | ❌ Not available | ❌ Not available |
| Loop components in OneNote \(Win32\) | ✅ Available | ❌ Not available | ❌ Not available | ❌ Not available | ❌ Not available |
| Loop components in Whiteboard | ✅ Available | ❌ Not available | ✅ Available | ❌ Not available | ❌ Not available |

For Teams integration details, see [Teams service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/teams-service-description).

For environments where a Loop experience is unavailable, users can't create that experience and admins can't enable it through policy. For policy behavior details, see [admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide#cloud-environment-availability).

Support for inserting Loop components in Word for the web was retired on September 1, 2025, and is scheduled to be retired in OneNote for the web beginning in mid-September 2026 \([MC1107493](https://admin.microsoft.com/#/MessageCenter/:/messages/MC1107493); [MC1454385](https://admin.microsoft.com/#/MessageCenter/:/messages/MC1454385)\). After each retirement takes effect, users can't insert new Loop components or use them as live, interactive components in the respective web app. Existing Loop components aren't removed or lost; they're replaced with links to the corresponding Loop pages, which users can continue to access and edit. The full Loop component experience continues to be available in the OneNote desktop app for Windows.

## Relationship to Copilot Pages and Copilot Notebooks

Loop My workspace shares a single user-owned SharePoint Embedded container with Copilot Pages and Copilot Notebooks. These are separate user experiences with separate admin settings, but they all read and write to the same physical personal container per user. The container is created when *either* the **Create Loop workspaces in Loop** policy *or* the **Create and view Copilot Pages and Copilot Notebooks** policy allows creation for the user; to prevent the container from being created, disable both policies for the same user. For the full explanation \(naming, lifecycle, and admin tools\), see [storage](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide).

## Related articles

- [Loop access via Microsoft 365 subscriptions](https://support.microsoft.com/office/loop-access-via-microsoft-365-subscriptions-92915461-4b14-49a4-9cd4-d1c259292afa)
- [Admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide)
- [UX examples for admin policy states](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-ux-examples?view=o365-worldwide)
- [Storage](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide)
- [Permissions](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-permission?view=o365-worldwide)
- [Summary of compliance capabilities](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-compliance-summary?view=o365-worldwide)
- [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Overview of Loop components in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-components-teams?view=o365-worldwide)
