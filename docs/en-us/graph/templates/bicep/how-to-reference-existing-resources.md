<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/how-to-reference-existing-resources -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Onboard existing Microsoft Graph resources in Bicep templates

You may need to reference and manage Microsoft Graph resources that were created outside of your Bicep templates. In this article, you learn how to:

- Reference existing Microsoft Graph resources in Bicep templates using a [client-provided key](https://learn.microsoft.com/en-us/graph/templates/bicep/concept-uniquely-named-resources#microsoft-graph-client-provided-keys)
- Onboard existing Microsoft Graph resources in Bicep files, allowing you to manage and redeploy them consistently.
- Onboard precreated resources for management and redeployment in Bicep files, and how to use the [`existing`](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/existing-resource) keyword to read their properties without redeploying.

## Prerequisites

To complete this article, you need:

- An Azure subscription. If you don't have one, [create a free account](https://azure.microsoft.com/free/).
- Least privileged permissions or roles to read or update the resource, or ownership of the resource. For guidance, see [Least privileged roles by task](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/delegate-by-task) and [Default user permissions](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions).
- [Install Bicep tools for authoring and deployment](https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-install-bicep-tools). This article uses VS Code with the Bicep extension for authoring and Azure CLI for deployment. You also get Azure PowerShell samples.
- Deploy Bicep files interactively or with zero-touch \(app-only\) deployment.

## Onboard existing Microsoft Graph resources for use in a Bicep file

If you have Microsoft Graph resources that weren't created with Bicep, onboard them for management in Bicep files. For example, you might want to update an existing application or deploy a security group that includes an existing group and service principal as members.

To reference an existing group in a Bicep file, set its **uniqueName** property. To reference an existing service principal if you don't know its **id** or **appId**, its parent application must have its **uniqueName** property set.

In this section:

- Add the **uniqueName** property to an existing group and application using Azure CLI or Azure PowerShell
- Update the existing application in a Bicep file
- Use the `existing` keyword in the Bicep file to get the ID of an existing group and service principal
- Configure a security group in the Bicep file with the existing group and service principal as members, and the service principal as an owner
- Deploy the Bicep file

### Step 1: Set the uniqueName property for the group and application

Set the **uniqueName** property for an existing group and application, for example, to `TestGroup-20241202` and `TestApp-20241202`, as shown in the following request.

Important

You can't change the `uniqueName` property after you set it.

- [Azure CLI](#tabpanel_1_CLI)
- [Azure PowerShell](#tabpanel_1_PowerShell)

```azurecli
# Sign in to Azure
az login

# Create a resource group
az group create --name exampleRG --location eastus

# Update the uniqueName property of the group and application
# Replace the IDs with your group and application IDs
az rest --method patch --url 'https://graph.microsoft.com/v1.0/groups/cec00de2-08b9-4081-aaf5-55d78ac9b4c4' --body '{\"uniqueName\": \"TestGroup-20241202\"}' --headers "content-type=application/json"
az rest --method patch --url 'https://graph.microsoft.com/v1.0/applications/25ae6414-05a1-4cce-9899-ad11d9eedde2' --body '{\"uniqueName\": \"TestApp-20241202\"}' --headers "content-type=application/json"
```

```azurepowershell
# Sign in to Azure
Connect-AzAccount

# Use the id (NOT appId) of the application you want to update
$appUri = 'https://graph.microsoft.com/v1.0/applications/25ae6414-05a1-4cce-9899-ad11d9eedde2'

# Use the id of the group you want to update
$groupUri = 'https://graph.microsoft.com/v1.0/groups/cec00de2-08b9-4081-aaf5-55d78ac9b4c4'

# Create JSON payloads to set the immutable uniqueName property
$appPayload = '{"uniqueName":"TestApp-20241202"}'
$groupPayload = '{"uniqueName":"TestGroup-20241202"}'

# Update the resources
Invoke-AzRestMethod -Uri $appUri -Method PATCH -Payload $appPayload
Invoke-AzRestMethod -Uri $groupUri -Method PATCH -Payload $groupPayload
```

### Step 2: Add existing group and service principal as members and owner of another group

Now use the `existing` keyword to reference the existing group and service principal, get their IDs, and add them to the **owners** and **members** collections of another group.

1. In VS Code, create two files in the same folder: *main.bicep* and *bicepconfig.json*.
2. Add the following code to **main.bicep**:

   ```Bicep
   extension 'br:mcr.microsoft.com/bicep/extensions/microsoftgraph/v1.0:1.0.0

   // Reference existing group
   resource group 'Microsoft.Graph/groups@v1.0' existing = {
     uniqueName: 'TestGroup-20241202'
   }

   // Update existing application and reference its service principal
   resource application 'Microsoft.Graph/applications@v1.0' = {
     uniqueName: 'TestApp-20241202'
     displayName: 'Updating the displayName to something new'
   }
   resource servicePrincipal 'Microsoft.Graph/servicePrincipals@v1.0' existing = {
     appId: application.appId
   }

   // Add preceding service principal and group as members of another group
   // Add preceding service principal as owner of the group. 
   // If Group-1 uniqueName doesn't exist, this is a new deployment.
   // If Group-1 uniqueName exists, this is a redeployment/update. For redeployments, existing members and owners are retained.
   resource group 'Microsoft.Graph/groups@v1.0' = {
     displayName: 'Group-1'
     mailEnabled: false
     mailNickname: 'Group-1'
     securityEnabled: true
     uniqueName: 'Group-1'
     members: [group.id, servicePrincipal.id]
     owners: [servicePrincipal.id]
   }
   ```

3. Deploy the Bicep file using Azure CLI or Azure PowerShell.

   - [Azure CLI](#tabpanel_2_CLI)
   - [Azure PowerShell](#tabpanel_2_PowerShell)


   ```azurecli
   # Create a resource group
   az group create --name exampleRG --location eastus

   # Deploy the Bicep file
   az deployment group create --resource-group exampleRG --template-file main.bicep
   ```


   ```azurepowershell
   New-AzResourceGroupDeployment -ResourceGroupName "exampleRG" -TemplateFile ".\main.bicep"
   ```

---

After deployment, you see a message that the deployment succeeded.

## Related content

- [Uniquely named resources](https://learn.microsoft.com/en-us/graph/templates/bicep/concept-uniquely-named-resources)
