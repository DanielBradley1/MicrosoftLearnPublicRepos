<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/grant-managed-identity-resource-access-powershell -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# Use PowerShell to grant a managed identity access to a resource

This article shows you how to use PowerShell to give a managed identity access to an Azure resource. In this article, we use the example of an Azure virtual machine \(Azure VM\) managed identity accessing an Azure storage account. Once you've configured an Azure resource with a managed identity, you can then give the managed identity access to another resource, similar to any security principal.

## Prerequisites

- Be sure you've enabled managed identity on an Azure resource, such as an [Azure virtual machine](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-configure-managed-identities).
- If you don't already have an Azure account, [sign up for a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before continuing.

## Use Azure RBAC to assign a managed identity access to another resource using PowerShell

Note

We recommend that you use the Azure Az PowerShell module to interact with Azure. See [Install Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell) to get started. To learn how to migrate to the Az PowerShell module, see [Migrate Azure PowerShell from AzureRM to Az](https://learn.microsoft.com/en-us/powershell/azure/migrate-from-azurerm-to-az).

To run the scripts in this example, you have two options:

- Use the [Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview), which you can open using the **Try It** button on the top-right corner of code blocks.
- Run scripts locally by installing the latest version of [Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell), then sign in to Azure using `Connect-AzAccount`.

1. Enable managed identity on an Azure resource, [such as an Azure VM](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-configure-managed-identities).
2. Give the Azure virtual machine \(VM\) access to a storage account.

   1. Use [Get-AzVM](https://learn.microsoft.com/en-us/powershell/module/az.compute/get-azvm) to get the service principal for the VM named `myVM`, which was created when you enabled managed identity.
   2. Use [New-AzRoleAssignment](https://learn.microsoft.com/en-us/powershell/module/az.resources/new-azroleassignment) to give the VM **Reader** access to a storage account called `myStorageAcct`:


   ```azurepowershell
   $spID = (Get-AzVM -ResourceGroupName myRG -Name myVM).identity.principalid
   New-AzRoleAssignment -ObjectId $spID -RoleDefinitionName "Reader" -Scope "/subscriptions/<mySubscriptionID>/resourceGroups/<myResourceGroup>/providers/Microsoft.Storage/storageAccounts/<myStorageAcct>"
   ```

## Next steps

- [Configure an application to trust a managed identity](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-config-app-trust-managed-identity?toc=/entra/identity/managed-identities-azure-resources/toc.json)
- [Use Azure Resources Extension in Visual Studio \(VS\) Code for Managed Identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/azure-resources-extension-managed-identities)
