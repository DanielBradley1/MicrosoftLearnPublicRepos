<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-see-monitor-results -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# View monitor results and manage monitors

Use the monitor experience to review monitor definitions, monitor run results, configuration drifts, baseline details, permissions readiness, settings, and audit logs. This article describes how to use the monitor pages after a monitor is created.

Configuration management supports operations in the home tenant and in other tenants that are connected through governance relationships. Monitor results and drift records describe resources in the monitor's target tenant.

## Prerequisites

- Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator).
- The tenant has licenses for **Tenant Governance Basic** or **Tenant Governance Premium**. Basic includes monitor results and drift reporting for the home tenant and governed tenants. See [Microsoft Entra Tenant Governance licensing](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/licensing).
- At least one configuration monitor exists in the tenant.
- The Tenant Configuration Management service has the permissions required to run the monitor. If a monitor run fails because of missing service permissions, [update the service permissions](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-permissions-tenant-monitoring) before you rely on later run results.
- To view drift in another tenant, verify that the governance relationship is active and that you have the required delegated access.

## View monitors

To view the configuration monitors in your tenant, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator).
2. Browse to **Tenant Governance**. Under **Tenant management**, select **Monitors** for the home tenant. Under **Other tenants**, select **Monitors \(Preview\)** for governed tenants.
3. For governed tenants, use the target-tenant filters to select the tenant you want to review.
4. On the **Monitors** tab, review monitor definitions, create a monitor, refresh the list, or select a monitor to open its details.

## View monitor results

To review the results of monitor runs, follow these steps:

1. Select the **Monitor results** tab.
2. Filter by target tenant to isolate home-tenant or governed-tenant runs.
3. Review the monitor name, monitor ID, target tenant, start time, completion time, run status, and number of detected drifts.

A monitor result summarizes a single monitor run. Use this page to identify failed or partially successful runs, and to find runs that detected configuration drift.

[![Screenshot of monitor results showing completion times, run status, and detected drift counts.](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/monitor-results.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/monitor-results.png#lightbox)

For governed-tenant runs, check the target tenant alongside the result.

[![Screenshot of governed-tenant monitor results with target tenants and detected drift counts.](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/governed-tenant-monitor-results.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/governed-tenant-monitor-results.png#lightbox)

## View configuration drifts

To review the configuration drifts a monitor detected, follow these steps:

1. Select the **Configuration drifts** tab.
2. Filter by target tenant to review drifts for the same scope as your monitor results.
3. Review the monitor, target tenant, resource name, resource type, drifted properties, and first detection time.
4. Select a drift record to compare current and expected property values.

A drift record identifies the resource and property that differ from the baseline. Confirm the target tenant when reviewing a drift. If you change tenant filters, check the selected scope on both the results and drifts pages; a tenant filter doesn't change a monitor's target or baseline.

[![Screenshot of configuration drifts showing affected resources, resource types, and drifted properties.](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/configuration-drifts.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/configuration-drifts.png#lightbox)

## Manage a monitor

To review and manage an individual monitor, follow these steps:

1. Select a monitor from the monitor list.
2. On **Overview**, review the **Details**, **Monitoring**, and **Audit** cards. **Details** shows the display name, description, creation date, and the services whose resources are monitored. The **Monitoring** card shows the last monitor run time, resource type, count, and configuration drifts. The **Audit** card shows audit events, such as monitor creation and update events, from the last 30 days, and the date of the last audit event.
3. On **Monitor results**, review the run history for the selected monitor.
4. On **Configuration drifts**, review the drift records for the selected monitor.
5. On **Baseline**, view, edit, or download the monitor baseline JSON.
6. On **Permissions**, review application and delegated permission readiness for the target tenant.
7. On **Settings**, view and manage the display name and description for the monitor.
8. On **Audit logs**, review the create and update events for the monitor.

## Related content

- [Configuration management](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/configuration-management)
- [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0&preserve-view=true)
- [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0&preserve-view=true)
- [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0&preserve-view=true)
- [Create a configuration monitor](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-monitor)
- [Update or delete a monitor](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-update-delete-monitor).
