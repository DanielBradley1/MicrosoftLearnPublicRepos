<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/assign-app-role-managed-identity-azure-cli -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# Assign an application role to a managed identity using Azure CLI

Managed identities for Azure resources provide Azure services with an identity in Microsoft Entra ID. They work without needing credentials in your code. Azure services use this identity to authenticate to services that support Microsoft Entra authentication. Application roles provide a form of role-based access control, and allow a service to implement authorization rules.

Note

The tokens your application receives are cached by the underlying infrastructure. This means that any changes to the managed identity's roles can take significant time to process. For more information, see [Limitation of using managed identities for authorization](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/managed-identity-best-practice-recommendations#limitation-of-using-managed-identities-for-authorization).

In this article, you'll learn how to assign a managed identity to an application role exposed by another application using the [Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview) or [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/what-is-azure-cli).

## Prerequisites

- If you're unfamiliar with managed identities for Azure resources, see [Managed identity for Azure resources overview](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).
- Review the [difference between a system-assigned and user-assigned managed identity](https://learn.microsoft.com/en-us/azure/logic-apps/authenticate-with-managed-identity).
- If you don't already have an Azure account, [sign up for a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before continuing.

## Assign a managed identity access to another application's app role using CLI

- Use the Bash environment in [Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview). For more information, see [Get started with Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/quickstart).

  [![](https://learn.microsoft.com/en-us/entra/reusable-content/azure-cli/media/hdi-launch-cloud-shell.png)](https://shell.azure.com)

- If you prefer to run CLI reference commands locally, [install](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) the Azure CLI. If you're running on Windows or macOS, consider running Azure CLI in a Docker container. For more information, see [How to run the Azure CLI in a Docker container](https://learn.microsoft.com/en-us/cli/azure/run-azure-cli-docker).

  - If you're using a local installation, sign in to the Azure CLI by using the [az login](https://learn.microsoft.com/en-us/cli/azure/reference-index#az-login) command. To finish the authentication process, follow the steps displayed in your terminal. For other sign-in options, see [Authenticate to Azure using Azure CLI](https://learn.microsoft.com/en-us/cli/azure/authenticate-azure-cli).
  - When you're prompted, install the Azure CLI extension on first use. For more information about extensions, see [Use and manage extensions with the Azure CLI](https://learn.microsoft.com/en-us/cli/azure/azure-cli-extensions-overview).
  - Run [az version](https://learn.microsoft.com/en-us/cli/azure/reference-index?#az-version) to find the version and dependent libraries that are installed. To upgrade to the latest version, run [az upgrade](https://learn.microsoft.com/en-us/cli/azure/reference-index?#az-upgrade).

1. Enable managed identity on an Azure resource, [such as an Azure virtual machines](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-configure-managed-identities).
2. Find the object ID of the managed identity's service principal.

   - **For a system-assigned managed identity**, you can find the object ID on the Azure portal on the resource's **Identity** page. You can also use the following script to find the object ID. You'll need the resource ID of the resource you created in the previous step, which is available in the Azure portal on the resource's **Properties** page.

     ```azurecli
     resourceIdWithManagedIdentity="/subscriptions/{my subscription ID}/resourceGroups/{my resource group name}/providers/Microsoft.Compute/virtualMachines/{my virtual machine name}"

     oidForMI=$(az resource show --ids $resourceIdWithManagedIdentity --query "identity.principalId" -o tsv | tr -d '[:space:]')
     echo "object id for managed identity is: $oidForMI"
     ```

   - **For a user-assigned managed identity**, you can find the managed identity's object ID on the Azure portal on the resource's **Overview** page. You can also use the following script to find the object ID. You'll need the resource ID of the user-assigned managed identity.

     ```azurecli
     userManagedIdentityResourceId="/subscriptions/{my subscription ID}/resourceGroups/{my resource group name}/providers/Microsoft.ManagedIdentity/userAssignedIdentities/{my managed identity name}"

     oidForMI=$(az resource show --id $userManagedIdentityResourceId --query "properties.principalId" -o tsv | tr -d '[:space:]')
     echo "object id for managed identity is: $oidForMI"
     ```

3. [Create a new application registration](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) to represent the service that your managed identity sends a request to.

   - If the API or service that exposes the app role grant to the managed identity already has a service principal in your Microsoft Entra tenant, skip this step.

4. Find the object ID of the service application's service principal. You can find this using the [Microsoft Entra admin center](https://entra.microsoft.com/).

   1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/).
   2. In the left nav blade, select **Entra ID** > **Enterprise apps**. Then find the application and look for the **Object ID**.
   3. You can also find the service principal's object ID by its display name using the following script:

      ```azurecli
      appName="{name for your application}"
      serverSPOID=$(az ad sp list --filter "displayName eq '$appName'" --query '[0].id' -o tsv | tr -d '[:space:]')
      echo "object id for server service principal is: $serverSPOID"
      ```


      Note


      Display names for applications are not unique, so you should verify that you obtain the correct application's service principal.

   4. Or you can find the Object ID by the unique Application ID for your application registration:

      ```azurecli
      appID="{application id for your application}"
      serverSPOID=$(az ad sp list --filter "appId eq '$appID'" --query '[0].id' -o tsv | tr -d '[:space:]')
      echo "object id for server service principal is: $serverSPOID"
      ```

5. Add an [app role](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to the application you created in the previous step. You can create the role using the Azure portal or using Microsoft Graph. For example, you could add an app role like this:

   ```json
   {
       "allowedMemberTypes": [
           "Application"
       ],
       "displayName": "Read data from MyApi",
       "id": "00001111-aaaa-2222-bbbb-3333cccc4444",
       "isEnabled": true,
       "description": "Allow the application to read data as itself.",
       "value": "MyApi.Read.All"
   }
   ```

6. Assign the app role to the managed identity. You'll need the following information to assign the app role:

   - `managedIdentityObjectId`: the object ID of the managed identity's service principal, which you found in step 2.
   - `serverServicePrincipalObjectId`: the object ID of the server application's service principal, which you found in step 4.
   - `appRoleId`: the ID of the app role exposed by the server app, which you generated in step 5 - in the example, the app role ID is `00000000-0000-0000-0000-000000000000`.

7. Execute the following script to add the role assignment. This functionality isn't directly exposed on the Azure CLI and that a REST command is used here instead:

   ```azurecli
   roleguid="00000000-0000-0000-0000-000000000000"
   az rest -m POST -u https://graph.microsoft.com/v1.0/servicePrincipals/$oidForMI/appRoleAssignments -b "{\"principalId\": \"$oidForMI\", \"resourceId\": \"$serverSPOID\",\"appRoleId\": \"$roleguid\"}"
   ```

## Next steps

- [Managed identity for Azure resources overview](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)
