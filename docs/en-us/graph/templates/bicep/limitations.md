<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/limitations -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Microsoft Graph Bicep feature limitations and restrictions

This article explains Microsoft Graph Bicep feature limitations and restrictions. You'll learn which features are unsupported and discover workarounds for these challenges. Some limitations come from the Microsoft Graph service or the Bicep extensibility service, while others are specific to the Microsoft Graph Bicep extension.

## Application passwords are not supported for applications and service principals

Application passwords \(secrets\), defined by `passwordCredentials`, aren't supported for the `applications` and `servicePrincipals` Bicep types. Only `keyCredentials` are supported. For example, see the [template sample](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/create-client-app-sp-with-kv-cert) that sets up an application with a key credential stored in Azure Key Vault. In some cases, you can use a credential-less approach, like [federated identity credentials for GitHub Actions](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/create-fic-for-github-actions).

If you need application passwords, use a DeploymentScript resource to call Microsoft Graph and [add a password](https://learn.microsoft.com/en-us/graph/api/application-addpassword).

## Deploying role-assignable groups is not supported

While you declare a [role-assignable group](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/groups-concept) in a Bicep template by setting the **isAssignableToRole** property to `true`, deploying the group fails, even if the application or user has the required permissions for both interactive and app-only deployment flows.

If you need role-assignable groups, use a **DeploymentScript** resource to call Microsoft Graph to create the group.

## Unsupported deployment features

These deployment features aren't supported for Bicep extensible resources, including Microsoft Graph resources:

- [Preview changes using what-if](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/deploy-what-if)
- Verbose output
- [Deployment stacks](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/deployment-stacks)
- The [Azure portal deployment details](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/deployment-history) page only shows Microsoft Graph resources for deployments run in debug mode, under the **Operations details** menu

## Related content

- [Microsoft Entra service limits and restrictions](https://learn.microsoft.com/en-us/entra/identity/users/directory-service-limits-restrictions)
- [Known issues: Microsoft Graph Bicep templates](https://learn.microsoft.com/en-us/graph/templates/bicep/known-issues-graph-bicep)
