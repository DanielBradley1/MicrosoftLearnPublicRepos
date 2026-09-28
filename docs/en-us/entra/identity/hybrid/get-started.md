<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/get-started -->
<!-- Sitemap-Last-Modified: 2025-04-09 -->

# Steps to start integrating with Microsoft Entra ID

If you're new to hybrid identity, then this documentation is the place that you want to start. If you haven't done so, familiarize yourself with the [What is hybrid identity?](https://learn.microsoft.com/en-us/entra/identity/hybrid/whatis-hybrid-identity) documentation before jumping in.

This document provides the steps that are required to integrate your on-premises Active Directory with Microsoft Entra ID. Integrating with Active Directory is the process of setting up synchronization for users and groups with Microsoft Entra ID. These steps differ slightly depending on which tool you use.

Use the [Choosing the right sync tool](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios) first, to determine which one is right for you. Use the next section, for the tool that was recommended for you.

## Cloud sync

Use these tasks if you're deploying cloud sync to integrate with Active Directory.

| Task | Description |
| --- | --- |
| [Determine which sync tool is correct for you](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios) | Use the wizard to determine whether cloud sync or Microsoft Entra Connect is the right tool for you. |
| [Review the cloud sync prerequisites](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-prerequisites) | Review the necessary prerequisites before getting started. |
| [Download and install the provisioning agent](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-install) | Download and install the Microsoft Entra provisioning agent. |
| [Configure cloud sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-configure) | Configure and tailor synchronization for your organization. |
| [Verify users are synchronizing](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/tutorial-single-forest#verify-users-are-created-and-synchronization-is-occurring) | Make sure it's working. |

## Microsoft Entra Connect

Use these tasks if you're deploying Microsoft Entra Connect to integrate with Active Directory.

| Task | Description |
| --- | --- |
| [Determine which sync tool is correct for you](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios) | Use the wizard to determine whether cloud sync or Microsoft Entra Connect is the right tool for you. |
| [Review the Microsoft Entra Connect prerequisites](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-install-prerequisites) | Review the necessary prerequisites before getting started. |
| [Review and choose an installation type](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-install-select-installation) | Determine whether you'll use express or custom installation. |
| [Download Microsoft Entra Connect](https://www.microsoft.com/download/details.aspx?id=47594) | Download Microsoft Entra Connect. |
| [Install and configure Microsoft Entra Connect express settings](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-install-express) | If you're using express settings, install and configure Microsoft Entra Connect with express settings. |
| [Install and configure Microsoft Entra Connect custom settings](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-install-custom) | If you're using custom settings, install and configure Microsoft Entra Connect with express settings. |
| [Perform post installation tasks](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-post-installation) | Perform the post installation tasks. |
| [Verify users are synchronizing](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/tutorial-single-forest#verify-users-are-created-and-synchronization-is-occurring) | Make sure it's working. |

## Next steps

- [Common scenarios](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios)
- [Tools for synchronization](https://learn.microsoft.com/en-us/entra/identity/hybrid/sync-tools)
- [Choosing the right sync tool](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios)
- [Prerequisites](https://learn.microsoft.com/en-us/entra/identity/hybrid/prerequisites)
