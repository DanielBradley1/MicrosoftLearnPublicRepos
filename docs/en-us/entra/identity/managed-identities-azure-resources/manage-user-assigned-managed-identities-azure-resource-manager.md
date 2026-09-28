<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/manage-user-assigned-managed-identities-azure-resource-manager -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# Manage user-assigned managed identities using Azure Resource Manager

Managed identities for Azure resources eliminate the need to manage credentials in code. You can use them to get a Microsoft Entra token for your applications. The applications can use the token when accessing resources that support Microsoft Entra authentication. Azure manages the identity so you don't have to.

There are two types of managed identities: system-assigned and user-assigned. System-assigned managed identities have their lifecycle tied to the resource that created them. This identity is restricted to only one resource, and you can grant permissions to the managed identity by using Azure role-based access control \(RBAC\). User-assigned managed identities can be used on multiple resources.

In this article, you create a user-assigned managed identity by using Azure Resource Manager. You can't list and delete a user-assigned managed identity by using a Resource Manager template. Use the other methods to list or delete a user-assigned managed identity.

## Prerequisites

- If you're unfamiliar with managed identities for Azure resources, check out the [overview section](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview). *Be sure to review the [difference between a system-assigned and user-assigned managed identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview#managed-identity-types)*.
- If you don't already have an Azure account, [sign up for a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you continue.

## Template creation and editing

Resource Manager templates help you deploy new or modified resources defined by an Azure resource group. Several options are available for template editing and deployment, both local and portal-based. You can:

- Use a [custom template from Azure Marketplace](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/deploy-portal#deploy-resources-from-custom-template) to create a template from scratch or base it on an existing common or [quickstart template](https://azure.microsoft.com/resources/templates/).
- Derive from an existing resource group by exporting a template. You can export them from either [the original deployment](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#export-resource-groups-to-templates) or from the [current state of the deployment](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#export-resource-groups-to-templates).
- Use a local [JSON editor \(such as VS Code\)](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/quickstart-create-templates-use-the-portal), and then upload and deploy by using PowerShell or the Azure CLI.
- Use the Visual Studio [Azure Resource Group project](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/create-visual-studio-deployment-project) to create and deploy a template.

## Create a user-assigned managed identity

To create a user-assigned managed identity, your account needs the [Managed Identity Contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#managed-identity-contributor) role assignment.

To create a user-assigned managed identity, use the following template. Replace the `<USER ASSIGNED IDENTITY NAME>` value with your own values.

Important

When you create user-assigned managed identities, the name must start with a letter or number, and may include a combination of alphanumeric characters, hyphens \(-\) and underscores \(\_\). For the assignment to a virtual machine or virtual machine scale set to work properly, the name is limited to 24 characters. For more information, see [FAQs and known issues](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/known-issues).

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "resourceName": {
          "type": "string",
          "metadata": {
            "description": "<USER ASSIGNED IDENTITY NAME>"
          }
        }
  },
  "resources": [
    {
      "type": "Microsoft.ManagedIdentity/userAssignedIdentities",
      "name": "[parameters('resourceName')]",
      "apiVersion": "2018-11-30",
      "location": "[resourceGroup().location]"
    }
  ],
  "outputs": {
      "identityName": {
          "type": "string",
          "value": "[parameters('resourceName')]"
      }
  }
}
```
