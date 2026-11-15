<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-update-delete-monitor -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Update or delete a monitor

This article describes how to update or delete a configuration monitor in the [Microsoft Entra admin center](https://entra.microsoft.com). You might update a monitor when your configuration baseline changes. Delete a monitor when the monitored resources are no longer important for your organization's security or compliance requirements.

These actions apply to monitors targeting the home tenant or other tenants connected through governance relationships. Check the monitor's target tenant before updating or deleting it.

## Prerequisites

- Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator).
- The tenant has licenses for **Tenant Governance Basic** or **Tenant Governance Premium**. Basic includes monitors targeting the home tenant and governed tenants. See [Microsoft Entra Tenant Governance licensing](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/licensing).
- At least one configuration monitor must exist in your tenant.
- For a monitor targeting another tenant, verify the governance relationship and required delegated permissions. Workload permissions must remain valid for subsequent runs.

## Update a monitor

To update an existing configuration monitor:

1. Browse to **Tenant Governance**. Under **Tenant management**, select **Monitors** for the home tenant. Under **Other tenants**, select **Monitors \(Preview\)** for a governed tenant.
2. Open the monitor and confirm the target tenant.
3. Use **Settings** to update its name or description, or **Baseline** to update its configuration.

Review the monitor settings, target tenant, baseline, and permission readiness in the update wizard. You can update the baseline by using JSON, a snapshot, or a configuration baseline template, as available in the wizard. For details about baseline selection and tenant scope, see [Create a configuration monitor](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-monitor).

Changing the tenant filter in the monitor list doesn't retarget an existing monitor. The governed tenant is read-only when you edit a monitor. Create a new monitor to target a different tenant.

When you update an existing configuration monitor, the updated settings replace the existing monitor definition.

Important

A baseline update hides previous monitor results and drift records. A name or description update is a metadata-only change; it doesn't replace the baseline. Preserve required evidence before changing the baseline.

These update types also apply to monitors targeting governed tenants. New results and drifts are produced on later runs. Updating a monitor changes its definition, not the configuration of the resources it monitors. Use a deployment to change resource settings.

For a template-linked monitor, the baseline is read-only. Edit the source template and use **Apply latest**, when available, to apply a new version after reviewing parameter values.

## Delete a monitor

Deleting a monitor can't be undone and stops future runs for that monitor. Preserve any associated monitor results and drift records you need before deletion. Don't rely on a deleted monitor as your history archive.

To delete a configuration monitor:

1. Browse to **Tenant Governance**. Under **Tenant management**, select **Monitors** for the home tenant. Under **Other tenants**, select **Monitors \(Preview\)** for a governed tenant.
2. Confirm the target tenant.
3. Find the monitor you want to delete.
4. Select the checkbox next to the monitor's name, then select **Delete** in the command bar. Alternatively, hover over the monitor name and select the delete icon that appears.
5. In the confirmation dialog, select **Delete**.
6. Select a monitor to enable **Delete** in the command bar.

[![Screenshot of a selected monitor with the Delete command enabled in the command bar.](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/selected-monitor.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/selected-monitor.png#lightbox)

Deleting an other-tenant monitor removes the selected monitor from its target tenant. It doesn't delete resources in the governed tenant, revert previously applied configuration, or terminate the governance relationship. Other monitors aren't affected.

Permission or relationship changes can prevent later runs of a governed-tenant monitor. Review those dependencies when you update the monitor; don't interpret a failed run as confirmation that no drift exists.

## Related content

- [Create a monitor](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-monitor)
- [See monitor results and configuration drifts](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-see-monitor-results)
- [Set up permissions for tenant monitoring](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-permissions-tenant-monitoring)
- [Configuration management](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/configuration-management)
