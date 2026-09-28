<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/govern-service-accounts -->
<!-- Sitemap-Last-Modified: 2024-02-16 -->

# Governing Microsoft Entra service accounts

There are three types of service accounts in Microsoft Entra ID: managed identities, service principals, and user accounts employed as service accounts. When you create service accounts for automated use, they're granted permissions to access resources in Azure and Microsoft Entra ID. Resources can include Microsoft 365 services, software as a service \(SaaS\) applications, custom applications, databases, HR systems, and so on. Governing Microsoft Entra service account is managing creation, permissions, and lifecycle to ensure security and continuity.

Learn more:

- [Securing managed identities](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-managed-identities)
- [Securing service principals](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-principal)

Note

We do not recommend user accounts as service accounts because they are less secure. This includes on-premises service accounts synced to Microsoft Entra ID, because they aren't converted to service principals. Instead, we recommend managed identities, or service principals, and the use of Conditional Access.

Learn more: [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)

## Plan your service account

Before creating a service account, or registering an application, document the service account key information. Use the information to monitor and govern the account. We recommend collecting the following data and tracking it in your centralized Configuration Management Database \(CMDB\).

| Data | Description | Details |
| --- | --- | --- |
| Owner | User or group accountable for managing and monitoring the service account | Grant the owner permissions to monitor the account and implement a way to mitigate issues. Issue mitigation is done by the owner, or by request to an IT team. |
| Purpose | How the account is used | Map the service account to a service, application, or script. Avoid creating multiuse service accounts. |
| Permissions \(Scopes\) | Anticipated set of permissions | Document the resources it accesses and permissions for those resources |
| CMDB Link | Link to the accessed resources, and scripts in which the service account is used | Document the resource and script owners to communicate the effects of change |
| Risk assessment | Risk and business effect, if the account is compromised | Use the information to narrow the scope of permissions and determine access to information |
| Period for review | The cadence of service account reviews, by the owner | Review communications and reviews. Document what happens if a review is performed after the scheduled review period. |
| Lifetime | Anticipated maximum account lifetime | Use this measurement to schedule communications to the owner, disable, and then delete the accounts. Set an expiration date for credentials that prevents them from rolling over automatically. |
| Name | Standardized account name | Create a naming convention for service accounts to search, sort, and filter them |

## Principle of least privileges

Grant the service account permissions needed to perform tasks, and no more. If a service account needs high-level permissions, evaluate why and try to reduce permissions.

We recommend the following practices for service account privileges.

### Permissions

- Don't assign built-in roles to service accounts

  - See, [`oAuth2PermissionGrant` resource type](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant)

- The service principal is assigned a privileged role

  - [Create a custom role in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-create)

- Don't include service accounts as members of any groups with elevated permissions

  - See, [Get-MgDirectoryRoleMember](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectoryrolemember):

> `Get-MgDirectoryRoleMember`, and filter for objectType "Service Principal", or use  
> `Get-MgServicePrincipal | % { Get-MgServicePrincipalAppRoleAssignment -ObjectId $_ }`

- See, [Introduction to permissions and consent](https://learn.microsoft.com/en-us/entra/identity-platform/permissions-consent-overview) to limit the functionality a service account can access on a resource
- Service principals and managed identities can use Open Authorization \(OAuth\) 2.0 scopes in a delegated context impersonating a signed-on user, or as service account in the application context. In the application context, no one is signed in.
- Confirm the scopes service accounts request for resources

  - If an account requests Files.ReadWrite.All, evaluate whether it needs File.Read.All
  - [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference)

- Ensure you trust the application developer, or API, with the requested access

### Duration

- Limit service account credentials \(client secret, certificate\) to an anticipated usage period
- Schedule periodic reviews of service account usage and purpose

  - Ensure reviews occur prior to account expiration

After you understand the purpose, scope, and permissions, create your service account, use the instructions in the following articles.

- [How to use managed identities for App Service and Azure Functions](https://learn.microsoft.com/en-us/azure/app-service/overview-managed-identity?tabs=dotnet)
- [Create a Microsoft Entra application and service principal that can access resources](https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal)

Use a managed identity when possible. If you can't use a managed identity, use a service principal. If you can't use a service principal, then use a Microsoft Entra user account.

## Build a lifecycle process

A service account lifecycle starts with planning, and ends with permanent deletion. The following sections cover how you monitor, review permissions, determine continued account usage, and ultimately deprovision the account.

### Monitor service accounts

Monitor your service accounts to ensure usage patterns are correct, and that the service account is used.

#### Collect and monitor service account sign-ins

Use one of the following monitoring methods:

- Microsoft Entra sign-in logs in the Azure portal
- Export the Microsoft Entra sign-in logs to

  - [Azure Storage documentation](https://learn.microsoft.com/en-us/azure/storage/)
  - [Azure Event Hubs documentation](https://learn.microsoft.com/en-us/azure/event-hubs/), or
  - [Azure Monitor Logs overview](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/data-platform-logs)

Use the following screenshot to see service principal sign-ins.

![Screenshot of service principal sign-ins.](https://learn.microsoft.com/en-us/entra/architecture/media/govern-service-accounts/service-accounts-govern-1.png)

#### Sign-in log details

Look for the following details in sign-in logs.

- Service accounts not signed in to the tenant
- Changes in sign-in service account patterns

We recommend you export Microsoft Entra sign-in logs, and then import them into a security information and event management \(SIEM\) tool, such as Microsoft Sentinel. Use the SIEM tool to build alerts and dashboards.

### Review service account permissions

Regularly review service account permissions and accessed scopes to see whether they can be reduced or eliminated.

- See, [Get-MgServicePrincipalOauth2PermissionGrant](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.applications/get-mgserviceprincipaloauth2permissiongrant)
- See, [`AzureADAssessment`](https://github.com/AzureAD/AzureADAssessment) and confirm validity
- Don't set service principal credentials to **Never expire**
- Use certificates or credentials stored in Azure Key Vault, when possible

  - [What is Azure Key Vault?](https://learn.microsoft.com/en-us/azure/key-vault/general/basic-concepts)

### Recertify service account use

Establish a regular review process to ensure service accounts are regularly reviewed by owners, security team, or IT team.

The process includes:

- Determine service account review cycle, and document it in your CMDB
- Communications to owner, security team, IT team, before a review
- Determine warning communications, and their timing, if the review is missed
- Instructions if owners fail to review or respond

  - Disable, but don't delete, the account until the review is complete

- Instructions to determine dependencies. Notify resource owners of effects

The review includes the owner and an IT partner, and they certify:

- Account is necessary
- Permissions to the account are adequate and necessary, or a change is requested
- Access to the account, and its credentials, are controlled
- Account credentials are accurate: credential type and lifetime
- Account risk score hasn't changed since the previous recertification
- Update the expected account lifetime, and the next recertification date

### Deprovision service accounts

Deprovision service accounts under the following circumstances:

- Account script or application is retired
- Account script or application function is retired. For example, access to a resource.
- Service account is replaced by another service account
- Credentials expired, or the account is non-functional, and there aren't complaints

Deprovisioning includes the following tasks:

After the associated application or script is deprovisioned:

- [Sign-in logs in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins) and resource access by the service account

  - If the account is active, determine how it's being used before continuing

- For a managed service identity, disable service account sign-in, but don't remove it from the directory
- Revoke service account role assignments and OAuth2 consent grants
- After a defined period, and warning to owners, delete the service account from the directory

## Next steps

- [Securing cloud-based service accounts](https://learn.microsoft.com/en-us/entra/architecture/secure-service-accounts)
- [Securing managed identities](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-managed-identities)
- [Securing service principal](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-principal)
