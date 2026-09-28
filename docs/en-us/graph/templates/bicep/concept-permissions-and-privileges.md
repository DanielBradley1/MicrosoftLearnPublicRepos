<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/concept-permissions-and-privileges -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Permissions and privileges for Microsoft Graph Bicep template deployments

To deploy a Bicep file, you need specific permissions for the resources in the file, and you need access to all actions on the Azure `Microsoft.Resources/deployments` resource type. You get permissions for Azure resources and Microsoft Graph resources in different ways. This article explains the differences and required privileges to deploy Bicep files that include both Azure and Microsoft Graph resources.

## Access scenarios

Azure and Microsoft Graph APIs support [two access scenarios](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#access-scenarios): *delegated access* and *app-only access*. In delegated \(interactive\) access, the app calls an API on behalf of a signed-in user. In app-only \(noninteractive\) access, the app calls an API with its own identity, without a signed-in user. Both scenarios are supported for Bicep deployments.

## Permission types in Azure vs. Microsoft Graph

Microsoft Graph APIs use two types of permissions: *delegated permissions* for delegated access, and *application permissions* for app-only access. Azure APIs have only one delegated permission and don't have application permissions.

Learn more about [Microsoft Graph permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types) with examples and comparisons.

## Permissions for delegated or interactive deployments

In interactive deployments, an app's privileges depend on the delegated permissions \(OAuth 2.0 scopes\) you grant it and the signed-in user's own permissions. The granted scopes show as the *scp* claim in the access token.

Azure Resource Manager APIs provide one delegated permission: *user\_impersonation*. The signed-in user's permissions depend on their assigned [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles). The app's privileges are limited to the Azure built-in roles assigned to the signed-in user.

Microsoft Graph APIs provide many [granular delegated permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#all-permissions), usually scoped to resource types. The signed-in user's permissions depend on their assigned roles in Microsoft Graph services, like [Microsoft Entra](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference), Teams, Exchange, and SharePoint. The app's privileges are limited to the intersection of the signed-in user's permissions and the granted delegated permissions.

Azure PowerShell and Azure CLI are supported for interactive deployments. These tools have the needed delegated permissions for Azure Resource Manager and Microsoft Graph \(Microsoft Entra ID\).

To deploy Microsoft Graph resources through Bicep files interactively:

- The signed-in user must be assigned the necessary [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) to deploy the Azure resources in the Bicep file.
- The signed-in user must be assigned the necessary Microsoft Graph service roles, like [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference), to deploy the Microsoft Graph resources in the Bicep file.
- The signed-in user must be assigned the necessary [Azure built-in role](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) that lets them deploy templates \(access to all operations on `Microsoft.Resources/deployments`\).

![Diagram that shows the permissions and privileges needed to deploy Azure and Microsoft Graph resources using Bicep templates in interactive scenarios.](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/permissions-and-privileges/delegated-deployments-highres.png)

## Permissions for app-only or zero-touch deployments

For app-only access, the app uses its own identity without a signed-in user. This scenario is common for automated deployments, like those run by build pipelines or GitHub Actions.

Azure Resource Manager APIs don't provide application permissions. Authorization depends on the [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) assigned to the app service principal.

Microsoft Graph APIs provide many [granular application permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#all-permissions) scoped to resource types. When an admin grants these permissions, they appear as *roles* claims in the access token for Microsoft Graph services.

To deploy Microsoft Graph resources through Bicep files without a signed-in user:

- The app's service principal must be assigned the necessary [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) to deploy the Azure resources in the Bicep file.
- The app's service principal must be assigned the necessary [Azure built-in role](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) that lets it deploy templates \(access to all operations on `Microsoft.Resources/deployments`\).
- The app must be granted the necessary application permissions to deploy the Microsoft Graph resources in the Bicep file. These permissions might be Microsoft Graph application permissions or [Microsoft Entra built-in or custom roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

![Diagram that shows permissions and privileges needed to deploy Azure and Microsoft Graph resources using Bicep templates in app-only scenarios.](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/permissions-and-privileges/app-only-deployments-highres.png)

## Enforce least privilege access

Always follow the *principle of least privilege*. Grant only the permissions the app needs to do its tasks. This approach reduces the attack surface if someone compromises the app.

For Microsoft Graph Bicep resources, see the [templates resource reference](https://learn.microsoft.com/en-us/graph/templates/bicep/reference/overview) to find the least privileged permissions each resource type supports.

Learn more about [enhancing security with the principle of least privilege](https://learn.microsoft.com/en-us/entra/identity-platform/secure-least-privileged-access).

## Related content

- [Overview of Microsoft Graph permissions](https://learn.microsoft.com/en-us/graph/permissions-overview)
