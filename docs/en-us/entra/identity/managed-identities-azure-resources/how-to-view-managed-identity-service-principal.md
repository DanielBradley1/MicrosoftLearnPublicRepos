<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-view-managed-identity-service-principal -->
<!-- Sitemap-Last-Modified: 2025-03-14 -->

# View the service principal of a managed identity

Managed identities for Azure resources provide Azure services with an automatically managed identity in Microsoft Entra ID. You can use this identity to authenticate to any service that supports Microsoft Entra authentication without having credentials in your code.

In this article, you'll learn how to view the service principal of a managed identity.

Note

Service principals are enterprise applications.

## Prerequisites

- If you're unfamiliar with managed identities for Azure resources, see [What are managed identities for Azure resources?](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).
- If you don't already have an Azure account, [sign up for a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before continuing.
- Enable [system assigned identity on a virtual machine](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/qs-configure-portal-windows-vm#system-assigned-managed-identity) or [application](https://learn.microsoft.com/en-us/azure/app-service/overview-managed-identity#add-a-system-assigned-identity).

## View the service principal for a managed identity using the Azure portal

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. Browse to **Entra ID** > **Enterprise apps**.
3. In the **Manage** section select **All applications**.
4. Set a filter for "Application type == Managed Identities" and select **Apply**.
5. \(Optional\) In the search filter box, enter the name of the Azure resource that has system managed identities enabled or the name of the user assigned managed identity.

   [![Screenshot of the View managed identity service principal.](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-service-principal-portal/view-managed-identity-service-principal-portal.png)](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-service-principal-portal/view-managed-identity-service-principal-portal.png#lightbox)

## Next steps

For more information about managed identities, see [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).

## View the service principal of a managed identity using Azure CLI

- Use the Bash environment in [Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview). For more information, see [Get started with Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/quickstart).

  [![](https://learn.microsoft.com/en-us/entra/reusable-content/azure-cli/media/hdi-launch-cloud-shell.png)](https://shell.azure.com)

- If you prefer to run CLI reference commands locally, [install](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) the Azure CLI. If you're running on Windows or macOS, consider running Azure CLI in a Docker container. For more information, see [How to run the Azure CLI in a Docker container](https://learn.microsoft.com/en-us/cli/azure/run-azure-cli-docker).

  - If you're using a local installation, sign in to the Azure CLI by using the [az login](https://learn.microsoft.com/en-us/cli/azure/reference-index#az-login) command. To finish the authentication process, follow the steps displayed in your terminal. For other sign-in options, see [Authenticate to Azure using Azure CLI](https://learn.microsoft.com/en-us/cli/azure/authenticate-azure-cli).
  - When you're prompted, install the Azure CLI extension on first use. For more information about extensions, see [Use and manage extensions with the Azure CLI](https://learn.microsoft.com/en-us/cli/azure/azure-cli-extensions-overview).
  - Run [az version](https://learn.microsoft.com/en-us/cli/azure/reference-index?#az-version) to find the version and dependent libraries that are installed. To upgrade to the latest version, run [az upgrade](https://learn.microsoft.com/en-us/cli/azure/reference-index?#az-upgrade).

The following command demonstrates how to view the service principal of a virtual machine \(VM\) or application with managed identity enabled. Replace `<Azure resource name>` with your own values.

```azurecli
az ad sp list --display-name <Azure resource name>
```

## Next steps

For more information on managing Microsoft Entra service principals, see [Azure CLI ad sp](https://learn.microsoft.com/en-us/cli/azure/ad/sp).

## View the service principal for a managed identity using PowerShell

To run the scripts for this example, you have two options:

- Use the [Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview), which you can open using the **Try It** button on the top right corner of code blocks.
- Run scripts locally by installing the latest version of [Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell), then sign in to Azure using `Connect-AzAccount`.

The following command demonstrates how to view the service principal of a virtual machine \(VM\) or application with *system assigned identity* enabled. Replace `<Azure resource name>` with your own values.

```powershell
Get-AzADServicePrincipal -DisplayName <Azure resource name>
```

## Next steps

For more information on viewing Microsoft Entra service principals using PowerShell, see [Get-AzADServicePrincipal](https://learn.microsoft.com/en-us/powershell/module/az.resources/get-azadserviceprincipal).
