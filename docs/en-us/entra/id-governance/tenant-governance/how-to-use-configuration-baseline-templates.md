<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-use-configuration-baseline-templates -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Use configuration baseline templates \(Preview\)

Use Configuration baseline templates to standardize baseline definitions across monitors and deployments. A template contains reusable baseline JSON; selecting it doesn't apply configuration until you create a deployment.

Configuration management supports operations in the home tenant and in other tenants that are connected through governance relationships.

## Prerequisites

- Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator).
- The tenant has licenses for **Tenant Governance Basic** or **Tenant Governance Premium**. Basic includes templates for home-tenant and cross-tenant configuration management. See [Microsoft Entra Tenant Governance licensing](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/licensing).
- Baseline JSON or a completed snapshot that contains the resource settings you want to reuse.
- Required workload permissions for operations that use the template. For deployments or monitors in another tenant, an active governance relationship and required delegated access.

For permission setup, see [Configure configuration management service permissions](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-permissions-tenant-monitoring).

## Create a template

To create a reusable baseline template, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator).
2. Browse to **Tenant Governance** > **Templates** > **Configuration Baseline Template**.
3. Select **New configuration template**.
4. In the **Configuration JSON** editor, provide the template metadata and baseline by uploading a JSON file, importing a completed snapshot, or composing JSON.
5. Review resource properties and tenant-specific references. If you imported a snapshot, verify that the captured settings represent your intended standard.
6. Select **Validate + Save**.

[![Screenshot of the Templates page with configuration baseline templates and the creation command.](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/configuration-baseline-templates.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/configuration-baseline-templates.png#lightbox)

## Edit a template

To update template metadata or its baseline, follow these steps:

1. Open the template from **Configuration Baseline Template**.
2. Update the template metadata or baseline in the **Configuration JSON** editor.
3. Select **Save changes**.

Saving an edit publishes a new template version. Review the monitors and deployments that should use the revised definition. Changing a template doesn't automatically update existing monitors or reapply configuration to tenants.

## Apply a template to a monitor

To monitor a tenant against the template baseline, follow these steps:

1. Browse to **Tenant Governance**. Under **Tenant management**, select **Monitors** for the home tenant, or under **Other tenants**, select **Monitors \(Preview\)** for a governed tenant. Select **New monitor**.
2. For a governed-tenant monitor, select the target on **Tenants**.
3. On **Configuration baseline**, choose the template option and select the approved template.
4. Review the baseline and target tenant, then complete permission checks and the remaining steps in [Create a configuration monitor](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-monitor).

## Apply a template to a deployment

To apply the template baseline to a tenant, follow these steps:

1. Browse to **Tenant Governance**. Under **Tenant management** or **Other tenants**, select **Configuration deployments** for the required scope, and select **Deploy configuration**.
2. For a governed-tenant deployment, select the target on **Tenants**.
3. On **Configuration baseline**, choose the template option and select the approved template.
4. Review the settings, tenant-specific references, and write permissions before completing [Create a configuration deployment](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-configuration-deployment).

## Manage template versions

Template edits create service-managed versions. Keep reviewed baseline JSON in version control, and record an owner, approval date, and intended environments for each approved revision.

Test a revision with a limited tenant scope before broader deployment. When replacing an existing baseline, explicitly review and update affected monitors or create deployments from the approved revision. Preserve a copy of the previous baseline for comparison and change review.

For a template-linked monitor, the baseline is read-only in the monitor details. Edit the source template, then use **Apply latest**, when available, to adopt the latest version. Review and supply any required parameter values before confirming.

If the service's template version limit is reached, the editor attempts to delete the oldest version that no monitor references and retries the save. If every earlier version is still referenced, update or delete the monitors using those versions before saving again. Keep your own approved baseline history rather than relying on every service version being retained.

## Related content

- [Configuration baseline templates](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/configuration-baseline-templates).
- [Create configuration snapshots](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-snapshots).
- [Create a configuration monitor](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-monitor).
- [Create a configuration deployment](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-configuration-deployment).
