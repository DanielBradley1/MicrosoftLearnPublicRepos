<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-permissions-tenant-monitoring -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Configure configuration management service permissions

Use the **Configuration management permissions** page to assign or remove permissions for the Tenant Configuration Management service. The service uses these permissions for snapshots, deployments, and monitors. Templates store baseline definitions; operations that use those definitions require the corresponding workload permissions.

Configure service permissions before running an operation that includes the corresponding workload resources. Missing permissions can cause incomplete snapshots, deployment failures, or failed monitor runs.

When you create a monitor or snapshot, the **Permissions** step shows whether the service has the least-privilege permissions for the resource types you selected. This step is read-only. If the wizard shows that required least-privilege permissions are missing, use the **Configuration management permissions** page to add them.

## Prerequisites

- Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator) to grant application or delegated permissions and assign Microsoft Entra roles to the service principal.
- For operations in another tenant, an active [governance relationship](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-relationships) and delegated administration access for the target tenant and workload. Review both relationship-level and workload-specific access in [Cross-tenant delegated administration](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/cross-tenant-delegated-administration).

## Choose application or delegated permissions

Use the **Application permissions** tab for app-only access used by the service to capture snapshots and run monitors. Use **Entra roles** for Microsoft Entra roles assigned to the service principal.

Use the **Delegated permissions** tab for configuration deployments. Deployments call workload APIs on behalf of the signed-in administrator and require delegated write permissions. Application permissions and roles assigned to the service principal don't satisfy the deployment wizard's delegated permission check. The administrator must also have the required workload roles.

For governed-tenant operations, also configure delegated administration through the governance relationship. This cross-tenant access doesn't replace the background service's application permissions for monitoring. Permission readiness for monitoring checks application permissions and service principal role assignments in the selected tenant; deployment readiness checks delegated write permissions.

## Open Configuration management permissions

To open the permissions page, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **Tenant Governance** > **Configuration management permissions**.

[![Screenshot of the Application permissions tab with permissions and the Add permissions command.](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/application-permissions.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/application-permissions.png#lightbox)

## Assign application permissions and roles

Assign permissions based on the workloads that contain the resources you want to snapshot, deploy, or monitor:

- **Microsoft Entra ID or Intune resources**: On the **Application permissions** tab, add the app-only permissions for the relevant Microsoft Graph resources.

  - For the permissions required to snapshot or monitor Microsoft Entra resources, see [Supported Microsoft Entra resources for Tenant Configuration Management](https://learn.microsoft.com/en-us/graph/utcm-entra-resources).
  - For the permissions required to snapshot or monitor Intune resources, see [Supported Microsoft Intune resources for Tenant Configuration Management](https://learn.microsoft.com/en-us/graph/utcm-intune-resources).

- **Teams resources**: On the **Entra roles** tab, assign the **Teams Reader** Microsoft Entra role.
- **Exchange Online resources**: On the **Application permissions** tab, assign **Exchange.ManageAsApp**. Then use Exchange Online PowerShell to assign Exchange roles to the Tenant Configuration Management service principal. For the steps, see [App-only authentication in Exchange Online PowerShell and Security & Compliance PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/app-only-auth-powershell-v2#step-2-assign-api-permissions-to-the-application).

  For the permissions required to snapshot or monitor Exchange resources, see [Supported Microsoft Exchange resources for Tenant Configuration Management](https://learn.microsoft.com/en-us/graph/utcm-exchange-resources).
- **Defender or Purview resources**: On the **Application permissions** tab, assign **Exchange.ManageAsApp**. Then use Security & Compliance PowerShell to assign Security and Compliance \(Defender and Purview\) roles to the Tenant Configuration Management service principal. For the steps, see [Connect to Security & Compliance PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-scc-powershell).

  For the permissions required to snapshot or monitor Defender or Purview resources, see [Supported Microsoft Security and Compliance resources for Tenant Configuration Management](https://learn.microsoft.com/en-us/graph/utcm-securityandcompliance-resources).

Note

The **Configuration management permissions** page doesn't show workload permissions that are assigned to the service within Exchange Online, Defender, or Purview. Use Exchange Online PowerShell or Security & Compliance PowerShell to assign and remove those permissions.

## Assign delegated permissions

Use the **Delegated permissions** tab to configure delegated access required by the operation and target workload:

1. Open **Configuration management permissions**.
2. Select the **Delegated permissions** tab.
3. Select **Add delegated permission**.
4. Select the delegated permissions required for the feature and target workload.
5. Grant admin consent when prompted as a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator).
6. Verify that the permissions appear in the list. Review their grant state on **Permissions** in the deployment wizard.

[![Screenshot of the Delegated permissions tab with sample permissions and the Add permissions command.](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/delegated-permissions.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tenant-governance-configuration-management/delegated-permissions.png#lightbox)

For other-tenant operations, also verify that the governance relationship is active and that the signed-in user has the delegated roles required in the governed tenant. Consent alone doesn't grant the user workload access.

If readiness shows missing permissions, resolve them before running the operation. The governed-tenant wizard's permission check is informational; reaching **Review** doesn't prove that all permissions or administrator roles are sufficient. A readiness check doesn't replace validation of service-local permissions in Exchange Online, Defender, or Purview.

## Remove permissions

Select the **Application permissions**, **Delegated permissions**, or **Entra roles** tab as appropriate. Select the checkbox next to the permission or role, and then select **Remove** in the command bar.

Removing permissions can affect later monitor runs or deployments that depend on them, including operations targeting governed tenants.

## Related content

- [Configuration management](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/configuration-management)
- [Set up authentication for Tenant Configuration Management APIs](https://learn.microsoft.com/en-us/graph/utcm-authentication-setup)
- [Exchange Online RBAC for applications](https://learn.microsoft.com/en-us/exchange/permissions-exo/application-rbac)
- [Microsoft Defender unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac)
- [Microsoft Purview permissions](https://learn.microsoft.com/en-us/purview/purview-permissions)
- [Use Microsoft Teams administrator roles to manage Teams](https://learn.microsoft.com/en-us/microsoftteams/using-admin-roles)
- [Role-based access control \(RBAC\) with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview)
