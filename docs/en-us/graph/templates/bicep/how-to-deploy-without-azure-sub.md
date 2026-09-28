<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/how-to-deploy-without-azure-sub -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Deploy Microsoft Graph resources without an Azure subscription

You can deploy Microsoft Graph resources using Bicep templates even if your tenant doesn't have an Azure subscription. This article explains how to deploy at the tenant scope, so you can automate Microsoft Graph resource deployment without Azure. This approach is useful when:

- Your organization doesn't use Azure services.
- You have an [Azure AD B2C tenant](https://learn.microsoft.com/en-us/azure/active-directory-b2c/overview) that can't support Azure subscriptions.
- You have a [Microsoft Entra external tenant](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations) that can't support Azure subscriptions.

Note

This method applies only if your Bicep template contains Microsoft Graph resources exclusively. If your template includes Azure resources, you need a valid Azure subscription.

## Prerequisites

- The tenant doesn't have any Azure subscriptions.
- The user and/or service principal deploying the Bicep file must have the minimum permissions required for the resources in the Bicep file.
- [Install Bicep tools for authoring and deployment](https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-install-bicep-tools). This article uses Visual Studio Code with the Bicep extension for authoring and Azure CLI for deployment. Azure PowerShell examples are also provided.
- You can deploy Bicep files interactively or using app-only \(zero-touch\) deployment.

## Deploy Microsoft Graph resources

Follow these steps to deploy Microsoft Graph resources at the tenant scope without an Azure subscription.

1. Assign deployment permissions to the principal:

   1. [Elevate account access to the User Access Administrator role](https://learn.microsoft.com/en-us/azure/role-based-access-control/elevate-access-global-admin) if needed.
   2. Assign deployment permissions to the user or service principal at the tenant \(`/`\) scope. Use one of the following methods, listed from least to most privileged:

      - Assign a [custom role](https://learn.microsoft.com/en-us/azure/role-based-access-control/custom-roles) with the `Microsoft.Resources/deployments/*` permission.
      - Assign a [built-in Azure DevOps role](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles/devops) with the `Microsoft.Resources/deployments/*` permission.
      - Assign the Owner or Contributor role.


   In the following request, <principalId> is the ID of the user \(in interactive deployments\) or service principal \(in app-only deployments\) deploying the resources; <principalType> is "user" or "servicePrincipal" for interactive or app-only deployments respectively.


   - [Azure CLI](#tabpanel_1_CLI)
   - [Azure PowerShell](#tabpanel_1_PowerShell)


   ```azurecli
   az role assignment create --assignee-object-id "<principalId>" --assignee-principal-type "<principalType>" --scope "/" --role "Owner"`
   ```


   ```azurepowershell
   New-AzRoleAssignment -ObjectId "<principalId>" -ObjectType "<principalType>" -Scope "/" -RoleDefinitionName "Owner"
   ```


   3. Remove the elevated access assignment when you're done.

2. Set the deployment scope in your Bicep file:

   - In your `main.bicep` file, add `targetScope = 'tenant'` at the top. The template must contain only Microsoft Graph resources.

3. Deploy at the tenant scope using the security principal with deployment privileges. Use [az deployment tenant create](https://learn.microsoft.com/en-us/cli/azure/deployment/tenant#az-deployment-tenant-create) or [New-AzTenantDeployment](https://learn.microsoft.com/en-us/powershell/module/az.resources/new-aztenantdeployment):

   - [Azure CLI](#tabpanel_2_CLI)
   - [Azure PowerShell](#tabpanel_2_PowerShell)


   ```azurecli
   az deployment tenant create --location WestUS --template-file main.bicep
   ```


   ```azurepowershell
   New-AzTenantDeployment -location "WestUS" -TemplateFile ".\main.bicep"
   ```


   - The `location` parameter is required and specifies where Azure Resource Manager stores deployment data.

## See also

- [Deploy to a tenant](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/deploy-to-tenant?tabs=azure-cli)
- [Understand deployment scopes](https://learn.microsoft.com/en-us/training/modules/deploy-resources-scopes-bicep/2-understand-deployment-scopes)
