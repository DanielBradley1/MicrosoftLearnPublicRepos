<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-create-bicep-zero-touch-mode -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Quickstart: Deploy a Bicep file as a service principal

This quickstart guides you to deploy a Bicep file with Microsoft Graph resources using app-only authentication \(noninteractive authentication\). This approach enables seamless integration into CI/CD pipelines for zero-touch deployments.

For delegated or interactive authentication, see [Create a Bicep file with Microsoft Graph resources](https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-create-bicep-interactive-mode).

## Prerequisites

- Have a Bicep file from [Create a Bicep file with Microsoft Graph resources](https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-create-bicep-interactive-mode).
- Own an Azure subscription.
- Be a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator) to assign Microsoft Graph app roles to a service principal.

## Create a service principal and assign an Azure role

Sign in to Azure CLI and create a service principal for deploying the Bicep file.

This example uses an application password \(client secret\) for simplicity and testing only. Assign the service principal the [Managed Identity Contributor role](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles/identity#managed-identity-contributor) scoped to a resource group.

Caution

Avoid using application passwords in production environments.

- [Azure CLI](#tabpanel_1_CLI)
- [Azure PowerShell](#tabpanel_1_PowerShell)

```azurecli
# Create a resource group
az group create --name exampleRG --location eastus

# Create a service principal with the Managed Identity Contributor role. Replace {myServicePrincipalName}, {mySubscriptionId}, and {myResourceGroupName} with your values.
az ad sp create-for-rbac --name {myServicePrincipalName} --role "Managed Identity Contributor" --scopes "/subscriptions/{mySubscriptionId}/resourceGroups/{myResourceGroupName}"
```

Output:

```output
{
  "appId": "myServicePrincipalId",
  "displayName": "myServicePrincipalName",
  "password": "myServicePrincipalPassword",
  "tenant": "myOrganizationTenantId"
}
```

**Copy the `password` value** — it can't be retrieved later.

```azurepowershell
$rg = New-AzResourceGroup -Name exampleRG -Location "eastus"

$sp = New-AzADServicePrincipal -DisplayName myServicePrincipalName
$tenantID = (Get-AzContext).Tenant.Id

New-AzRoleAssignment -ApplicationId $sp.AppId -RoleDefinitionName 'Managed Identity Contributor' -Scope $rg.ResourceId
```

Use these variables to [sign in as the service principal](#sign-in-as-service-principal-to-deploy-the-bicep-file).

## Assign Microsoft Graph permissions to the service principal

Grant the *Group.ReadWrite.All* application-only permission to the service principal using [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph). The Privileged Role Administrator role allows you to assign the required *AppRoleAssignment.ReadWrite.All* and *Application.Read.All* permissions.

Caution

Limit access to apps granted the *AppRoleAssignment.ReadWrite.All* permission. See [AppRoleAssignment.ReadWrite.All](https://learn.microsoft.com/en-us/graph/permissions-reference#approleassignmentreadwriteall) for details.

```powershell
# Authenticate to Microsoft Graph
Connect-MgGraph -Scopes "AppRoleAssignment.ReadWrite.All","Application.Read.All"

# Find the service principal created earlier
$mySP = Get-MgServicePrincipalByAppId -AppId "myServicePrincipalId"

# Find the Microsoft Graph service principal
$graphSP = Get-MgServicePrincipalByAppId -AppId "00000003-0000-0000-c000-000000000000"

# Assign Group.ReadWrite.All app-only permission
New-MgServicePrincipalAppRoleAssignedTo -ResourceId $graphSP.Id -ServicePrincipalId $graphSP.Id -PrincipalId $mySP.Id -AppRoleId "62a82d76-70ea-41e2-9197-370581804d09"
```

## Sign in as service principal to deploy the Bicep file

Sign in using the service principal created earlier.

- [CLI](#tabpanel_2_CLI)
- [PowerShell](#tabpanel_2_PowerShell)

```azurecli
# Sign in with the service principal. This sample uses the Bash console.
spID=$(az ad sp list --display-name myServicePrincipalName --query "[].{spID:appId}" --output tsv)
tenantID=$(az ad sp list --display-name myServicePrincipalName --query "[].{tenantID:appOwnerOrganizationId}" --output tsv)
echo "Using appId $spID in tenant $tenantID"

az login --service-principal --username $spID --password {paste your SP password here} --tenant $tenantID
```

```azurepowershell
# Use the application ID as the username and the secret as the password
$securePassword = ConvertTo-SecureString "SP-password" -AsPlainText -Force
$credential = New-Object System.Management.Automation.PSCredential("SP-AppId", $securePassword)
Connect-AzAccount -ServicePrincipal -Credential $credential -Tenant $tenantID
```

Important

To avoid displaying your password on console when using `az login` interactively, use the `read -s` command in `bash`.

```bash
read -sp "Azure password: " AZ_PASS && echo && az login --service-principal -u <app-id> -p $AZ_PASS --tenant <tenant>
```

## Deploy the Bicep file

Deploy the Bicep file using the resource group's scope.

- [CLI](#tabpanel_3_CLI)
- [PowerShell](#tabpanel_3_PowerShell)

```azurecli
az deployment group create --resource-group exampleRG --template-file main.bicep
```

```azurepowershell
New-AzResourceGroupDeployment -ResourceGroupName exampleRG -TemplateFile ./main.bicep
```

Note

Deployment may fail due to replication delays when adding the managed service identity \(MSI\) as an owner of the Microsoft Entra group. Wait and retry the deployment.

## Clean up resources

Use Azure CLI or Azure PowerShell to delete the Azure resources and Microsoft Graph resources when no longer needed.

Note

Resource groups are an Azure concept and have no effect on Microsoft Graph resources. Microsoft Graph resources need to be cleaned up with another request to Microsoft Graph. For this you can use Azure CLI or Azure PowerShell, or [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview).

The following examples show commands to delete the Azure resource first then the Microsoft Graph resources using Azure CLI and Azure PowerShell.

- [CLI](#tabpanel_4_CLI)
- [PowerShell](#tabpanel_4_PowerShell)

```azurecli
# Delete the resource group
az group delete --name exampleRG

# Delete the Microsoft Graph group
az rest --method delete --url 'https://graph.microsoft.com/v1.0/groups%28uniqueName=%27myExampleGroup%27%29'

# Delete the client service principal
spID=$(az ad sp list --display-name myServicePrincipalName --query "[].{spID:id}" --output tsv)
az ad sp delete --id $spID
```

```azurepowershell
Remove-AzResourceGroup -Name exampleRG

$uri = 'https://graph.microsoft.com/v1.0/groups%28uniqueName=%27myExampleGroup%27%29'
Invoke-AzRestMethod -Uri $Uri -Method Delete

Remove-AzADServicePrincipal -ApplicationId $sp.AppId
```
