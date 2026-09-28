<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/workflows-environment-workflows-agents -->
<!-- Sitemap-Last-Modified: 2026-09-01 -->

# Microsoft Copilot workflows environment for Copilot workflows experiences

The *Microsoft Copilot workflows environment* is a special purpose Power Platform environment. When users in your tenant first use one of the *Copilot workflows experiences* in Microsoft Copilot—such as Workflows agents—Power Platform automatically creates it. This environment supports runtime operations required by the Copilot workflows experiences. It is created and governed differently than typical environments.

This article provides details about the environment's characteristics, behavior, permissions, and limitations. As a Power Platform or Microsoft 365 administrator, it can help you understand and manage the environment appropriately.

## Environment provisioning

When a user with a Copilot license uses one of the Copilot workflows experiences for the first time, Power Platform automatically creates the *Microsoft Copilot workflows* environment. It creates the environment, with Dataverse, in the region in or closest to the default region of your organization's Microsoft Entra tenant.

You don't need to take any manual steps to create this environment. It only creates one environment per tenant. The environment isn't visible in the Power Platform admin center environment list, or any Maker portals. Only workflows created by the *Copilot workflows experiences* in Microsoft Copilot are stored in this environment, which tenant admins can view in Power Platform admin center inventory.

The environment isn't deletable once created. However, since the environment's sole purpose is to house the workflows created by the Copilot workflows experiences in the tenant, the environment and flows created within are auto disabled and locked down in this instance: if a tenant admin disables Workflows agents from Microsoft 365 admin center. This control disables the environment as a whole, so it affects all Copilot workflows experiences in the tenant, not just Workflows agents.

## App and connection usage

Power Platform creates a security role for the environment named **M365 Workflows Agents Maker.** It also assigns this role to the users in the tenant, which provides users with permission to use the Copilot workflows experiences and save in the environment.

Note

By default, users aren't given **Environment Maker** permissions.

Users don't have direct access to create any artifact other than flows from the Copilot workflows experiences, as the environment is hidden from all Maker portals.

## Data loss prevention \(DLP\)

The Microsoft Copilot workflows environment has a fixed data loss prevention \(DLP\) policy:

All connectors are blocked, except for a set of connectors used by the *Copilot workflows experiences* that include:

- Microsoft Teams
- Outlook \(Office 365 Outlook\)
- Planner
- Approvals
- SharePoint
- AI action, AI prompt
- Microsoft Copilot actions

This environment limits the use to the previous set of allowlisted connectors only in the context of flows created by the Copilot workflows experiences.

Important

Tenant-level and environment-level DLP policies don't apply to the **Microsoft Copilot workflows** environment. Tenant admins have environment admin privileges to this environment to perform DSR export and delete.

## Frequently asked questions

This section contains answer to frequently asked questions about the workflows environment.

### What triggers the creation of the Microsoft Copilot workflows environment?

Power Platform creates the environment when a Copilot-licensed user in the tenant uses one of the Copilot workflows experiences for the first time.

### What license or app does the user require?

The user must be assigned a Microsoft Copilot license with the Microsoft Copilot with Graph-grounded chat app for the user to be provisioned in the environment.

### Can I delete the Microsoft Copilot workflows environment?

No.

### Does this environment consume storage from my tenant's entitlement?

No. For storage that this environment uses, Power Platform excludes it from your tenant's capacity calculations. It also doesn't appear on capacity pages.

### Can I apply custom DLP policies to this environment?

No. Power Platform governs this environment with a fixed DLP policy. Tenant or environment-level policies don't apply to this environment.

### Can users create custom apps, flows, or bots in this environment?

No. In the environment, Power Platform limits to only flows created by the *Copilot workflows experiences* and with the set of allowlisted connectors.
