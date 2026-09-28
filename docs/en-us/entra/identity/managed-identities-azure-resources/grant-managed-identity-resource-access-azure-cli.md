<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/grant-managed-identity-resource-access-azure-cli -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# Use Azure CLI to grant a managed identity access to a resource

This article shows you how to use the Azure CLI to give a managed identity access to an Azure resource. In this article, we use the example of an Azure virtual machine \(Azure VM\) managed identity accessing an Azure storage account. Once you've configured an Azure resource with a managed identity, you can then give the managed identity access to another resource, similar to any security principal.

## Prerequisites

- Be sure you've enabled managed identity on an Azure resource, such as an [Azure virtual machine](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-configure-managed-identities).
- If you don't already have an Azure account, [sign up for a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before continuing.

## Prepare your environment

- Use the Bash environment in [Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview). For more information, see [Get started with Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/quickstart).

  [![](https://learn.microsoft.com/en-us/entra/reusable-content/azure-cli/media/hdi-launch-cloud-shell.png)](https://shell.azure.com)

- If you prefer to run CLI reference commands locally, [install](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) the Azure CLI. If you're running on Windows or macOS, consider running Azure CLI in a Docker container. For more information, see [How to run the Azure CLI in a Docker container](https://learn.microsoft.com/en-us/cli/azure/run-azure-cli-docker).

  - If you're using a local installation, sign in to the Azure CLI by using the [az login](https://learn.microsoft.com/en-us/cli/azure/reference-index#az-login) command. To finish the authentication process, follow the steps displayed in your terminal. For other sign-in options, see [Authenticate to Azure using Azure CLI](https://learn.microsoft.com/en-us/cli/azure/authenticate-azure-cli).
  - When you're prompted, install the Azure CLI extension on first use. For more information about extensions, see [Use and manage extensions with the Azure CLI](https://learn.microsoft.com/en-us/cli/azure/azure-cli-extensions-overview).
  - Run [az version](https://learn.microsoft.com/en-us/cli/azure/reference-index?#az-version) to find the version and dependent libraries that are installed. To upgrade to the latest version, run [az upgrade](https://learn.microsoft.com/en-us/cli/azure/reference-index?#az-upgrade).

## Use Azure RBAC to assign a managed identity access to another resource

1. In this example, you give an Azure virtual machine \(VM\) managed access to a storage account. First use [az resource list](https://learn.microsoft.com/en-us/cli/azure/resource#az-resource-list) to get the service principal for a VM named myVM:

   ```azurecli
   spID=$(az resource list -n myVM --query [*].identity.principalId --out tsv)
   ```


   For an Azure Virtual Machine \(VM\) scale set, the command is the same except here you get the service principal for the VM set named "DevTestVMSS":


   ```azurecli
   spID=$(az resource list -n DevTestVMSS --query [*].identity.principalId --out tsv)
   ```

2. Once you have the service principal ID, use [az role assignment create](https://learn.microsoft.com/en-us/cli/azure/role/assignment#az-role-assignment-create) to give the virtual machine or virtual machine scale set **Reader** access to a storage account called "myStorageAcct":

   ```azurecli
   az role assignment create --assignee $spID --role 'Reader' --scope /subscriptions/<mySubscriptionID>/resourceGroups/<myResourceGroup>/providers/Microsoft.Storage/storageAccounts/myStorageAcct
   ```

## Related content

- [Configure an application to trust a managed identity](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-config-app-trust-managed-identity?toc=/entra/identity/managed-identities-azure-resources/toc.json)
- [Use Azure Resources Extension in Visual Studio \(VS\) Code for Managed Identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/azure-resources-extension-managed-identities)
