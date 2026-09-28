<!-- Source: https://learn.microsoft.com/en-us/graph/templates/terraform/quickstart-create-terraform -->
<!-- Sitemap-Last-Modified: 2025-08-09 -->

# Quickstart: Create and deploy your first Terraform configuration with Microsoft Graph resources

In this quickstart, you create a Terraform configuration that declares a Microsoft Entra security group and a managed service identity \(MSI\), representing a Microsoft Graph resource and an Azure resource respectively. You then add the MSI as an owner of the group. Finally, you deploy the Terraform configuration using a signed-in user.

Important

The `msgraph` provider for Terraform is currently in PREVIEW. See the [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) for legal terms that apply to Azure features that are in beta, preview, or otherwise not yet released into general availability.

## Prerequisites

- [Install and configure Terraform](https://learn.microsoft.com/en-us/azure/developer/terraform/quickstart-configure)
- [Install the Microsoft Terraform VS Code Extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureterraform)
- [Install and configure Microsoft Graph for PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/)
- Have a **Microsoft Entra role** that assigns you permissions to create a security group. [Users have this permission by default](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#compare-member-and-guest-default-permissions). However, [admins can turn off this default](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#restrict-member-users-default-permissions) in which case you need to be assigned at least the [Groups Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#groups-administrator) role.

## Add a Microsoft Graph application group

Note

The sample code for this article is located in the [MSGraph Terraform GitHub repo](https://github.com/microsoft/terraform-provider-msgraph/blob/main/examples/quickstarts/applications/).

See more [articles and sample code showing how to use Terraform to manage Azure resources](https://learn.microsoft.com/en-us/azure/developer/terraform)

1. Create a directory in which to test the sample Terraform code and make it the current directory.
2. Create a file called `providers.tf` and insert the following code:

```hcl
terraform {
  required_providers {
    msgraph = {
      source = "microsoft/msgraph"
    }
  }
}

provider "msgraph" {
}
```

3. Create a file named `main.tf` and insert the following code:

```hcl
resource "msgraph_resource" "group" {
  url = "groups"
  body = {
    displayName     = "My Group"
    mailEnabled     = false
    mailNickname    = "mygroup"
    securityEnabled = true
  }
}
```

When you hit \[CTRL + SPACE\] after typing `url = `, a list of resource types is displayed. Continue typing **groups** until you can select **groups** from the available options.

![Screenshot of selecting Microsoft Graph groups for resource type.](https://learn.microsoft.com/en-us/graph/templates/terraform/media/graph-terraform-authoring.png)

Tip

If you don't see the intellisense options in VS Code, make sure you installed the Terraform extension as specified in [Prerequisites](#prerequisites). If you installed the extension, give the extension some time to start after opening your Terraform configuration.

You can also use the `api_version` property to specify the API version. Always select v1.0 unless it's unavailable or the resource properties you need are only available in beta. For this quickstart, we do not set the version since it defaults to v1.0.

## Add a managed identity resource

VS Code with the `AzAPI` extension simplifies development by providing code samples, such as a sample that creates a managed identity. In main.tf, type create an `azapi_resource` called `managedidentity` and specify the type as `Microsoft.ManagedIdentity/userAssignedIdentities@2024-11-30`. Hit \[ENTER\] then press \[CTRL\] and \[SPACE\] together to see an option `code sample` \(you may need to hit the arrow keys to get to this option\). Press \[ENTER\].

![Screenshot of adding a resource snippet.](https://learn.microsoft.com/en-us/graph/templates/terraform/media/graph-terraform-code-sample.png)

1. Your resource should now look like this:

```hcl
resource "azapi_resource" "managedidentity" {
  type                      = "Microsoft.ManagedIdentity/userAssignedIdentities@2024-11-30"
  parent_id                 = "The id of the Microsoft.Resources/resourceGroups@2020-06-01 resource"
  name                      = "The name of the resource"
  location                  = "location"
  schema_validation_enabled = false
  response_export_values    = ["*"]
}
```

We will fix this after we define the resource group.

2. Go into your `providers.tf` file and update the code as follows:

```hcl
terraform {
  required_providers {
    msgraph = {
      source = "microsoft/msgraph"
    }
    azapi = {
      source = "Azure/azapi"
      version = "~>2.0"
    }
    random = {
      source  = "hashicorp/random"
      version = "~>3.0"
    }
  }
}

provider "msgraph" {
}

provider "azapi" {
}
```

The `random` provider helps us in our later step of creating a resource group.

3. Create a new file `variables.tf` and insert the following code:

```hcl
variable "resource_group_location" {
  type        = string
  default     = "swedencentral"
  description = "Location of the resource group."
}

variable "resource_group_name_prefix" {
  type        = string
  default     = "rg"
  description = "Prefix of the resource group name that's combined with a random ID so name is unique in your Azure subscription."
}
```

4. In your `main.tf` **add** the following code:

```hcl
# Create a resource group with a random name.
resource "random_pet" "rg_name" {
  prefix = var.resource_group_name_prefix
}

resource "azapi_resource" "rg" {
  type     = "Microsoft.Resources/resourceGroups@2020-06-01"
  location = var.resource_group_location
  name     = random_pet.rg_name.id
}
```

5. Also in your `main.tf` **modify** the existing `managedidentity` resource to look like this:

```hcl
resource "azapi_resource" "managedidentity" {
  type      = "Microsoft.ManagedIdentity/userAssignedIdentities@2024-11-30"
  parent_id = azapi_resource.rg.id
  location  = var.resource_group_location
  name      = "myManagedIdentity"
  response_export_values = {
    principal_id = "properties.principalId"
  }
}
```

6. Create a file `outputs.tf` and insert the following code:

```hcl
output "resource_group_name" {
  value = azapi_resource.rg.name
}

output "group_id" {
  value = msgraph_resource.group.id
}
```

## Make the managed identity an owner of the group resource

Now we will create a new `msgraph_resource` to make our managed identity the owner of the group.

**Add** to `main.tf` the following code:

```hcl
resource "msgraph_resource" "group_owner" {
  url =  "groups/${msgraph_resource.group.id}/owners/$ref"
  body = {
    "@odata.id" = "https://graph.microsoft.com/v1.0/servicePrincipals/${azapi_resource.managedidentity.output.principal_id}"
  }
}
```

HashiCorp Configuration language \(HCL\) enables us to specify expressions within strings, which is how we pass in the group ID and output from the managed identity resource. Now we've made an implicit reference to the managed identity's principal ID by inserting `resource.azapi_resource.managedidentity.output.principal_id` as the value of the array.

Note

The `azapi` and `msgraph` providers both utilize `response_exports_values` to store user-specified outputs. In this case we configured `response_exports_values` in the `managedidentity` resource as a map, but you can also configure it as a list. For more info on how to query values, [refer to the guide on the Terraform registry](https://registry.terraform.io/providers/Azure/azapi/latest/docs/guides/feature_jmes_query).

Your `main.tf` file should now look like this:

```hcl
resource "msgraph_resource" "application" {
  url = "groups"
  body = {
    displayName     = "My Group"
    mailEnabled     = false
    mailNickname    = "mygroup"
    securityEnabled = true
    owners = [resource.azapi_resource.managedidentity.id]
  }
}

# Create a resource group with a random name.
resource "random_pet" "rg_name" {
  prefix = var.resource_group_name_prefix
}

resource "azapi_resource" "rg" {
  type     = "Microsoft.Resources/resourceGroups@2020-06-01"
  location = var.resource_group_location
  name     = random_pet.rg_name.id
}

resource "azapi_resource" "managedidentity" {
  type = "Microsoft.ManagedIdentity/userAssignedIdentities@2024-11-30"
  location = var.resource_group_location
  name = "myManagedIdentity"
  response_export_values = {
    principal_id = "properties.principalId"
  }
}

resource "msgraph_resource" "group_owner" {
  url =  "groups/${msgraph_resource.group.id}/owners/$ref"
  body = {
    "@odata.id" = "https://graph.microsoft.com/v1.0/servicePrincipals/${azapi_resource.managedidentity.output.principal_id}"
  }
}
```

Now we are ready to deploy our code!

## Authenticate

If you haven't yet, make sure you've [authenticated to Azure](https://learn.microsoft.com/en-us/azure/developer/terraform/authenticate-to-azure).

Also make sure you've [authenticated to Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/authentication-commands):

```azurepowershell
Connect-MgGraph
```

## Initialize Terraform

Run [terraform init](https://www.terraform.io/docs/commands/init.html) to initialize the Terraform deployment. This command downloads the Azure provider required to manage your Azure resources.

```console
terraform init -upgrade
```

**Key points:**

- The `-upgrade` parameter upgrades the necessary provider plugins to the newest version that complies with the configuration's version constraints.

## Create a Terraform execution plan

Run [terraform plan](https://www.terraform.io/docs/commands/plan.html) to create an execution plan.

```console
terraform plan -out main.tfplan
```

**Key points:**

- The `terraform plan` command creates an execution plan, but doesn't execute it. Instead, it determines what actions are necessary to create the configuration specified in your configuration files. This pattern allows you to verify whether the execution plan matches your expectations before making any changes to actual resources.
- The optional `-out` parameter allows you to specify an output file for the plan. Using the `-out` parameter ensures that the plan you reviewed is exactly what is applied.

## Apply a Terraform execution plan

Run [terraform apply](https://www.terraform.io/docs/commands/apply.html) to apply the execution plan to your cloud infrastructure.

```console
terraform apply main.tfplan
```

**Key points:**

- The example `terraform apply` command assumes you previously ran `terraform plan -out main.tfplan`.
- If you specified a different filename for the `-out` parameter, use that same filename in the call to `terraform apply`.
- If you didn't use the `-out` parameter, call `terraform apply` without any parameters.

Note

Due to replication delays, adding the managed service identity \(MSI\) as an owner of the Microsoft Entra group may cause the deployment to fail. Wait a little and then deploy the same Terraform configuration again.

## Verify the results

### Azure

1. Get the Azure resource group name.

   ```console
   $resource_group_name=$(terraform output -raw resource_group_name)
   ```

2. Run [Get-AzResourceGroup](https://learn.microsoft.com/en-us/powershell/module/az.resources/Get-AzResourceGroup) to display the resource group.

   ```azurepowershell
   Get-AzResourceGroup -Name $resource_group_name
   ```

3. If successful, your results should look like this:

   ```json
   {
     "id": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg-crisp-panda",
     "location": "swedencentral",
     "managedBy": null,
     "name": "rg-crisp-panda",
     "properties": {
       "provisioningState": "Succeeded"
     },
     "tags": null,
     "type": "Microsoft.Resources/resourceGroups"
   }
   ```

### Microsoft Graph

1. Get the Group ID.

   ```console
   $group_id=$(terraform output -raw group_id)
   ```

2. Run [Get-MgGroup](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.groups/get-mggroup) to display the application group.

   ```azurepowershell
   Get-MgGroup -GroupId $group_id
   ```

3. If successful, your results should look like this:

   ```console
   DisplayName Id                                   MailNickname Description GroupTypes
   ----------- --                                   ------------ ----------- ----------
   My Group    00000000-0000-0000-0000-000000000000 mygroup                  {}
   ```

## Clean up resources

When you no longer need the resources created via Terraform, do the following steps:

1. Run [terraform plan](https://www.terraform.io/docs/commands/plan.html) and specify the `destroy` flag.

   ```console
   terraform plan -destroy -out main.destroy.tfplan
   ```


   **Key points:**


   - The `terraform plan` command creates an execution plan, but doesn't execute it. Instead, it determines what actions are necessary to create the configuration specified in your configuration files. This pattern allows you to verify whether the execution plan matches your expectations before making any changes to actual resources.
   - The optional `-out` parameter allows you to specify an output file for the plan. Using the `-out` parameter ensures that the plan you reviewed is exactly what is applied.

2. Run [terraform apply](https://www.terraform.io/docs/commands/apply.html) to apply the execution plan.

   ```console
   terraform apply main.destroy.tfplan
   ```

---

## Next step

1. Understand [Terraform](https://learn.microsoft.com/en-us/azure/developer/terraform/overview), its uses, and structure and syntax of Terraform files.
2. Explore [Learn modules for Terraform on Azure](https://learn.microsoft.com/en-us/training/paths/terraform-fundamentals/).
