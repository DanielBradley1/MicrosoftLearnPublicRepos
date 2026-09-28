<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/deployment-guide -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Deploy Microsoft Entra Tenant Governance end to end

This article describes how to deploy Microsoft Entra Tenant Governance across your organization. The deployment follows five phases: verifying prerequisites, discovering related tenants, establishing governance relationships, implementing delegated administration, and setting up configuration monitoring.

Each phase builds on the previous one. Complete the phases in order, but skip optional phases if they don't apply to your environment.

## Prerequisites

Before you begin, confirm that your environment meets these requirements:

- A Microsoft Entra tenant with the appropriate license for Tenant Governance. For details, see [Microsoft Entra licensing](https://learn.microsoft.com/en-us/entra/fundamentals/licensing#microsoft-entra-tenant-governance).
- An account with the Tenant Governance Administrator or Global Administrator role.
- For configuration management: an account with the Global Administrator or Privileged Role Administrator role.
- For secure tenant creation: either a paid [Enterprise Agreement \(EA\)](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/understand-ea-roles) or [Pay-As-You-Go](https://azure.microsoft.com/pricing/offers/ms-azr-0003p?cid=msft_learn) subscription. Both [Microsoft Online Subscription Agreement \(MOSA\)](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/view-all-accounts#microsoft-online-services-program) and [Microsoft Customer Agreement \(MCA\)](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/view-all-accounts#microsoft-customer-agreement) billing accounts are supported. You also need the required Azure Resource Manager \(ARM\) permissions for the selected subscription through the Tenant Contributor or Subscription Owner/Creator role. To identify your billing account type, see [View your billing accounts in the Azure portal](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/view-all-accounts).

## Phase 1: Enable related tenant discovery

Tenant discovery identifies other Microsoft Entra tenants that have observable relationships with your tenant. These relationships are based on signals such as B2B collaboration, multitenant application usage, and shared billing accounts. For more information about what related tenants represent, see [Related tenants](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/related-tenants).

### Enable related tenants

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a Tenant Governance Administrator.
2. Browse to **Tenant governance** > **Related tenants**.
3. Review the description of the tenant discovery feature.
4. Select **Discover related tenants**.

Important

Enabling tenant discovery is permanent. After you enable it, the setting can't be reversed.

Discovery signals begin aggregating after you enable the feature. It might take several days for data to populate. For more information about the signals and metrics that tenant discovery uses, see [Signals and metrics for tenant discovery](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/signals-metrics).

### Review and classify discovered tenants

After signals aggregate, review the related tenants inventory and classify each tenant:

1. Browse to **Tenant governance** > **Related tenants** to see the full list.
2. Examine the discovery signals for each tenant: B2B collaboration, multitenant applications, and shared billing accounts.
3. Compare initial and recent metrics to determine whether activity is ongoing, growing, or dormant.
4. Classify each tenant into one of these categories:

   - **Known and acceptable**: Clearly identifiable tenants \(partners, vendors, customers\) with expected activity. Document as a known relationship. No immediate governance action is needed.
   - **Requires governance**: Internal-looking tenants with moderate or growing activity and unclear ownership. Investigate and consider establishing a governance relationship.
   - **Potentially risky**: Unknown tenants with unexpected activity and no clear business justification. Consider quarantining. For more information, see [Quarantine unsanctioned tenants](https://learn.microsoft.com/en-us/entra/fundamentals/quarantine-unsanctioned-tenants).

For detailed guidance on interpreting discovery data, see [Interpret tenant discovery data](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-interpret-discovery-data).

## Phase 2: Create governance policy templates

Before you establish governance relationships, create one or more governance policy templates. A policy template defines the permissions and applications that are provisioned when a governance relationship is created.

### Create a policy template

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a Tenant Governance Administrator.
2. Browse to **Tenant governance** > **Templates**.
3. Select **Create template**.
4. Configure the template:

   - **Cross-tenant delegated administration**: Select the Microsoft Entra built-in roles to assign, and specify the security groups in the governing tenant that receive those roles.
   - **Multitenant applications** \(optional\): Select custom applications to provision in governed tenants.

5. Save the template.

Policy template updates don't automatically apply to existing governance relationships. To apply changes, send a new governance request and have the governed tenant accept it. For more information, see [Governance policy templates](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates).

### Configure a default policy template \(optional\)

If you plan to use the secure add-on tenant creation feature, configure a default policy template. The default template is applied automatically when a new governed tenant is created through that flow.

1. Create or update a policy template with the ID `default`.
2. Configure the delegated administration roles and applications for new tenants.

If no default template exists, new tenants created through the secure add-on flow don't automatically get a governance relationship. For more information, see [Create a governed tenant](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-tenant).

## Phase 3: Set up governance relationships

Governance relationships connect a governing tenant to one or more governed tenants. The process depends on whether the tenants share a billing account. For background on governance relationships, see [Governance relationships](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-relationships).

### Two-step handshake \(related tenants with shared billing accounts\)

Use the two-step process when a billing signal exists between the tenants:

**Step 1: Send a governance request \(governing tenant\)**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a Tenant Governance Administrator.
2. Browse to **Tenant governance** > **Governed tenants**.
3. Select **Send governance request**.
4. Select the target tenant and the policy template to apply.
5. Send the request. The request is valid for 14 days.

**Step 2: Accept the request \(governed tenant\)**

1. Sign in to the governed tenant as a Tenant Governance Administrator.
2. Browse to **Tenant governance** > **Governing tenants** > **Received requests**.
3. Review the request details, including the roles and applications defined in the policy template.
4. Select **Accept**.

### Three-step handshake \(tenants without shared billing\)

Use the three-step process when no billing signal exists between the tenants:

**Step 1: Send an invitation \(governed tenant\)**

1. Sign in to the governed tenant as a Tenant Governance Administrator.
2. Browse to **Tenant governance** > **Governing tenants** > **Sent invitations**.
3. Send an invitation to the future governing tenant. The invitation is valid for 30 days.

**Step 2: Send a governance request \(governing tenant\)**

1. Enable governance invitations in **Tenant governance** > **Settings** \(if not already enabled\).
2. Browse to **Tenant governance** > **Governed tenants** > **Received invitations**.
3. Review the invitation and send a governance request with the selected policy template. The request is valid for 14 days.

**Step 3: Accept the request \(governed tenant\)**

1. Browse to **Tenant governance** > **Governing tenants** > **Received requests**.
2. Review and accept the request.

### Verify the relationship

After the governed tenant accepts the request, verify that these resources are provisioned:

- A governance relationship object in both tenants
- Cross-tenant access settings updates
- GDAP role assignments \(if delegated administration is configured\)
- Service principals for multitenant applications \(if application management is configured\)

For complete setup instructions, see [Set up a governance relationship](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-governance-relationship).

## Phase 4: Implement cross-tenant delegated administration

After you establish governance relationships with delegated administration configured, administrators in the governing tenant can manage governed tenants without local or B2B accounts. For background, see [Cross-tenant delegated administration](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/cross-tenant-delegated-administration).

### Add users to security groups

Add the administrators who need cross-tenant access to the security groups specified in the governance policy template.

### Sign in to governed tenants

Administrators sign in to governed tenants by accessing a supported admin portal with the governed tenant's domain or ID:

1. Open the admin portal URL with the governed tenant identifier appended, for example: `https://entra.microsoft.com/{governed-tenant-domain-or-id}`
2. Sign in with governing tenant credentials.
3. Perform administrative tasks based on the assigned roles.

Supported admin portals include the Azure portal, Microsoft Entra admin center, Microsoft Intune, Exchange, SharePoint, Teams, and Microsoft 365 admin centers.

### Update delegated administration roles

To change the roles assigned through a governance relationship:

1. Update the governance policy template in the governing tenant.
2. Send a new governance request to the governed tenant with the updated template.
3. The governed tenant reviews and accepts the request to apply the updated roles.

For more information, see [Use cross-tenant delegated administration](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-delegated-administration) and [Monitor governing tenant admin activity](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-monitor-governing-activity).

## Phase 5: Set up configuration management

Configuration management lets you define a desired configuration state and monitor tenants for drift. Set up monitoring in each tenant where you want to detect configuration changes. For background, see [Configuration management](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/configuration-management).

### Set up permissions

The configuration management service requires explicit permissions to read tenant configuration.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a Global Administrator or Privileged Role Administrator.
2. Browse to **Tenant governance** > **Configuration management permissions**.
3. On the **Application permissions** tab, add the required Microsoft Graph application permissions for the resource types you want to monitor \(for example, `Policy.Read.All` for conditional access policies\).
4. On the **Entra roles** tab, assign any required roles \(for example, Teams Reader for Teams resources\).
5. For Exchange, Security, and Compliance resources, assign permissions in the respective service admin centers.

For detailed instructions, see [Set up permissions for tenant monitoring](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-permissions-tenant-monitoring).

### Author a configuration baseline

A configuration baseline is a JSON representation of the desired tenant configuration state.

1. Decide which resources and properties to monitor.
2. Author a JSON baseline manually, or generate a starting baseline by using Snapshot APIs to extract the current configuration.
3. Edit the baseline to define the desired state you want to enforce.

Each baseline can include up to 200 resource instances. The overall daily limit is 800 resource instances across all monitors.

For more information, see [Configuration management](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/configuration-management).

### Create a monitor

1. Browse to **Tenant governance** > **Configuration management** > **Monitors**.
2. Select **Create monitor**.
3. On the **Permissions** step, review and grant the required permissions for the resources in your baseline.
4. On the **Configuration baseline** step, paste or upload your JSON baseline. Validate the baseline before you proceed.
5. On the **Review** step, confirm the monitor name, description, and resource count.
6. Select **Create monitor**.

The monitor runs automatically every six hours. Results and drift data are available after the first run, which might take up to six hours.

For more information, see [Create a configuration monitor](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-monitor).

### Review results and address drift

1. Browse to **Tenant governance** > **Configuration management** > **Monitors**.
2. Select the **Monitor results** tab to view execution summaries.
3. Select the **Configuration drifts** tab to view detected drifts.
4. For each drift, select the **Drifted properties** value to see a comparison of actual and expected values.

To address a drift, either update the resource to match the baseline or update the baseline to reflect the acceptable current state. The next monitor run automatically marks the drift as resolved.

For more information, see [See monitor results and configuration drifts](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-see-monitor-results).

## Create governed tenants \(optional\)

Use the secure add-on tenant creation feature to create new tenants that are immediately governed.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) with the Tenant Contributor or Subscription Owner/Creator role for the selected subscription.
2. Create a new tenant using the **Governed Workforce** option.
3. Select the Azure subscription and resource group for the Microsoft Entra ID Free billing asset.

The system creates the tenant, establishes a governance relationship using the default policy template, provisions a billing asset, and adds the tenant to your related tenants inventory.

Note

A default governance policy template must be configured before you use this feature. If no default template exists, the tenant is created but no governance relationship is established.

For more information, see [Create a governed workforce tenant](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-tenant).

## Related content

- [What is Microsoft Entra Tenant Governance?](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/overview)
- [Related tenants](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/related-tenants)
- [Governance relationships](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-relationships)
- [Governance policy templates](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates)
- [Cross-tenant delegated administration](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/cross-tenant-delegated-administration)
- [Configuration management](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/configuration-management)
- [Microsoft Entra licensing](https://learn.microsoft.com/en-us/entra/fundamentals/licensing#microsoft-entra-tenant-governance)
- [Frequently asked questions](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/faq)
