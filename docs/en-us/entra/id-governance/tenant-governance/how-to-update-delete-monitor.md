<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-update-delete-monitor -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# Update or delete a monitor

This article describes how to update or delete a configuration monitor in the [Microsoft Entra admin center](https://entra.microsoft.com). You might update a monitor when your configuration baseline changes. Delete a monitor when the monitored resources are no longer important for your organization's security or compliance requirements.

## Prerequisites

- Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator).
- Your tenant must have a license for Microsoft Entra Tenant Governance.
- At least one configuration monitor must exist in your tenant.

## Update a monitor

To update an existing configuration monitor:

1. Browse to **Tenant Governance** > **Configuration management** > **Monitors**.
2. Find the monitor you want to update and select the edit \(pencil\) icon next to its name.

The update wizard uses the same steps as creating a monitor: **Permissions** → **Configuration baseline** → **Review**.

When you update an existing configuration monitor, the updated settings replace the existing monitor definition.

Important

When you update an existing monitor, Tenant Governance automatically deletes all previously generated monitor results and configuration drifts. The updated monitor records results and drifts again each time it runs.

## Delete a monitor

Deleting a monitor can't be undone. When you delete a monitor, Tenant Governance also immediately deletes all associated monitor results and configuration drifts.

To delete a configuration monitor:

1. Browse to **Tenant Governance** > **Configuration management** > **Monitors**.
2. Find the monitor you want to delete.
3. Select the checkbox next to the monitor's name, then select **Delete** in the command bar. Alternatively, hover over the monitor name and select the delete icon that appears.
4. In the confirmation dialog, select **Delete**.

## Related content

- [Create a monitor](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-monitor)
- [See monitor results and configuration drifts](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-see-monitor-results)
- [Set up permissions for tenant monitoring](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-permissions-tenant-monitoring)
- [Configuration management](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/configuration-management)
