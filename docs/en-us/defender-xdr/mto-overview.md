<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/mto-overview -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Microsoft Defender multitenant management

Multitenant management for Microsoft Defender XDR and Microsoft Sentinel in the Defender portal provides your security operations teams with a single, unified view of all the tenants you manage. This view enables your teams to quickly investigate incidents and perform advanced hunting across data from multiple tenants, improving your security operations.

## Microsoft Sentinel support

For each tenant, the Defender portal allows you to connect to one primary workspace and multiple secondary workspaces for Microsoft Sentinel. In the context of this article, a workspace is a Log Analytics workspace with Microsoft Sentinel enabled.

If you have tenants with Microsoft Sentinel workspaces onboarded to the Defender portal, you can:

- Triage incidents and alerts across Security Information and Event Management \(SIEM\) and eXtended Detection and Response \(XDR\) data.
- Proactively search for SIEM and XDR data across multiple tenants.
- Manage cases across multiple tenants.

Each workspace must be onboarded to the Defender portal for each of your tenants separately, as you would in a single-tenant scenario.

For more information, see:

- [Connect Microsoft Sentinel to Microsoft Defender XDR](https://learn.microsoft.com/en-us/azure/sentinel/microsoft-sentinel-onboard)
- [Multitenant organizations documentation](https://learn.microsoft.com/en-us/azure/active-directory/multi-tenant-organizations/)
- [Multiple Microsoft Sentinel workspaces in the Defender portal](https://learn.microsoft.com/en-us/azure/sentinel/workspaces-defender-portal)

## Feature availability

Multitenant management is also available to US government customers. Refer to the following table for specific scenarios for GCC, GCC High, DoD, and Commercial customers.

| Scenario | Availability |
| --- | --- |
| Multitenant management | Available to all GCC, GCC High, DoD, and Commercial customers. |
| Cross-cloud collaboration | - Both DoD and GCC High customers can manage tenants in each other's clouds.  <br>  <br>- GCC customers can manage tenants in the Commercial cloud. |

## Benefits of multitenant management

Some of the key benefits you get with multitenant management for Defender XDR and the Microsoft Sentinel in the Defender portal include:

- **A centralized place to manage incidents and cases across tenants**: A unified view provides SOC analysts with all the information they need to investigate incidents and cases across multiple tenants, eliminating the need to sign in and out of each one.
- **Streamlined threat hunting**: Multi-tenancy support enables SOC teams use Microsoft Defender XDR advanced hunting capabilities to create Kusto Query Language \(KQL\) queries that proactively hunt for threats across multiple tenants.
- **Multi-customer management for partners**: Managed Security Service Provider \(MSSP\) partners can now gain visibility into cases, security incidents, alerts, and threat hunting across multiple customers through a single pane of glass.

## What does multitenant management include?

The following key capabilities are available for each tenant you have access to in multitenant management for Microsoft Defender XDR and Microsoft Sentinel in the Defender portal:

| Capability | Description |
| --- | --- |
| **Incidents & alerts** > **[Incidents](https://learn.microsoft.com/en-us/defender-xdr/mto-incidents-alerts)** | Manage incidents originating from multiple tenants. |
| **Incidents & alerts** > **[Alerts](https://learn.microsoft.com/en-us/defender-xdr/mto-incidents-alerts)** | Manage alerts originating from multiple tenants. |
| **[Cases](https://learn.microsoft.com/en-us/defender-xdr/mto-manage-cases)** | Manage cases originating from multiple tenants. |
| **Hunting** > **[Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/mto-advanced-hunting)** | Proactively hunt for intrusion attempts and breach activity across multiple tenants at the same time. |
| **Hunting** > **[Custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detections-overview)** | View and manage custom detection rules across multiple tenants. |
| **Assets** > **Devices** > **[Tenants](https://learn.microsoft.com/en-us/defender-xdr/mto-tenant-devices)** | For all tenants and at a tenant-specific level, explore the device counts across different values such as device type, device value, onboarding status, and risk status. |
| **Endpoints** >**Vulnerability Management** > **[Dashboard](https://learn.microsoft.com/en-us/defender-xdr/mto-dashboard)** | The Microsoft Defender Vulnerability Management dashboard provides both security administrators and security operations teams with aggregated vulnerability management information across multiple tenants. |
| **Endpoints** > **Vulnerability management** > **[Tenants](https://learn.microsoft.com/en-us/defender-xdr/mto-dashboard)** | For all tenants and at a tenant-specific level, explore vulnerability management information across different values such as exposed devices, security recommendations, weaknesses, and critical CVEs. |
| **Configuration** > **Settings** | Lists the tenants you have access to. Use this page to view and manage your tenants. |
| **Multi-tenant management** > **[Tenant groups](https://learn.microsoft.com/en-us/defender-xdr/mto-tenant-groups)** | Organize the tenants you manage into named groups and switch the multitenant view between those groups. |

## Limitations

Mutitenant management supports multitenant single workspaces. This means that you can query multiple tenants and their primary workspace through Advanced Hunting without Lighthouse. [Azure Lighthouse](https://learn.microsoft.com/en-us/azure/lighthouse/) is required when you want to query a secondary workspace in a different tenant \(from Advanced Hunting, analytic rules, workbooks, etc.\). For these queries, use the workspace\(\) operator from either the multitenant management portal or `security.microsoft.com`.

## Next steps

- [Set up Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-requirements)
- [Create and manage tenant groups](https://learn.microsoft.com/en-us/defender-xdr/mto-tenant-groups)
