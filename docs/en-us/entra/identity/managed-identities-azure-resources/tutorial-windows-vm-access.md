<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/tutorial-windows-vm-access -->
<!-- Sitemap-Last-Modified: 2025-02-28 -->

# Tutorial: Use a system-assigned managed identity on a VM to access Azure Resource Manager

This quickstart shows you how to use a system-assigned managed identity as a virtual machine \(VM\)'s identity to access the Azure Resource Manager API. Managed identities for Azure resources are automatically managed by Azure and enable you to authenticate to services that support Microsoft Entra authentication without needing to insert credentials into your code.

You'll learn how to:

- Grant your virtual machine \(VM\) access to a resource group in Azure Resource Manager
- Get an access token using a virtual machine \(VM\) identity and use it to call Azure Resource Manager

## Use a Windows VM system-assigned managed identity to access resource manager

This tutorial explains how to create a system-assigned identity, assign it to a Windows Virtual Machine \(VM\), and then use that identity to access the [Azure Resource Manager](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview) API. Managed Service Identities are automatically managed by Azure. They enable authentication to services that support Microsoft Entra authentication, without needing to embed credentials into your code.

You'll learn how to:

- Grant your VM access to Azure Resource Manager.
- Get an access token by using the VM's system-assigned managed identity to access Resource Manager.

1. Sign in to the [Azure portal](https://portal.azure.com) with your administrator account.
2. Navigate to the **Resource Groups** tab.
3. Select the **Resource Group** that you want to grant the VM's managed identity access.
4. In the left panel, select **Access control \(IAM\)**.
5. Select **Add**, then select **Add role assignment**.
6. In the **Role** tab, select **Reader**. This role allows view all resources, but doesn't allow you to make any changes.
7. In the **Members** tab, for the **Assign access to** option, select **Managed identity**, then select **+ Select members**.
8. Ensure the proper subscription is listed in the **Subscription** dropdown. For **Resource Group**, select **All resource groups**.
9. For the **Manage identity** dropdown, select **Virtual Machine**.
10. For **Select**, choose your VM in the dropdown, then select **Save**.

    ![Screenshot that shows adding the reader role to the managed identity.](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/msi-tutorial-linux-vm-access-arm/msi-permission-linux.png)

## Get an access token

Use the VM's system-assigned managed identity and call the Resource Manager to get an access token.

To complete these steps, you need an SSH client. If you're using Windows, you can use the SSH client in the [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/about). If you need assistance configuring your SSH client's keys, see [How to Use SSH keys with Windows on Azure](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/ssh-from-windows), or [How to create and use an SSH public and private key pair for Linux VMs in Azure](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/mac-create-ssh-keys).

1. In the portal, navigate to your Linux VM and in the **Overview**, select **Connect**.
2. **Connect** to the VM with the SSH client of your choice.
3. In the terminal window, using `curl`, make a request to the local managed identities for Azure resources endpoint to get an access token for Azure Resource Manager. The `curl` request for the access token is below.

```bash
curl 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https://management.azure.com/' -H Metadata:true
```

Note

The value of the `resource` parameter must be an exact match for what is expected by Microsoft Entra ID. In the case of the Resource Manager's resource ID, you must include the trailing slash on the URI.

The response includes the access token you need to access Azure Resource Manager.

Response:

```json
{
  "access_token":"eyJ0eXAiOi...",
  "refresh_token":"",
  "expires_in":"3599",
  "expires_on":"1504130527",
  "not_before":"1504126627",
  "resource":"https://management.azure.com",
  "token_type":"Bearer"
}
```

Use this access token to access Azure Resource Manager; for example, to read the details of the resource group to which you previously granted this VM access. Replace the values of `<SUBSCRIPTION-ID>`, `<RESOURCE-GROUP>`, and `<ACCESS-TOKEN>` with the ones you created earlier.

Note

The URL is case-sensitive, so ensure if you are using the exact case as you used earlier when you named the resource group, and the uppercase “G” in “resourceGroup”.

```bash
curl https://management.azure.com/subscriptions/<SUBSCRIPTION-ID>/resourceGroups/<RESOURCE-GROUP>?api-version=2016-09-01 -H "Authorization: Bearer <ACCESS-TOKEN>" 
```

The response back with the specific resource group information:

```json
{
"id":"/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/resourceGroups/DevTest",
"name":"DevTest",
"location":"westus",
"properties":
{
  "provisioningState":"Succeeded"
  }
} 
```

## Use a Linux VM system-assigned managed identity to access a resource group in resource manager

This tutorial explains how to create a system-assigned identity, assign it to a Linux Virtual Machine \(VM\), and then use that identity to access the [Azure Resource Manager](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview) API. Managed Service Identities are automatically managed by Azure. They enable authentication to services that support Microsoft Entra authentication, without needing to embed credentials into your code.

You learn how to:

- Grant your VM access to Azure resource manager.
- Get an access token by using the VM's system-assigned managed identity to access resource manager.

1. Sign in to the [Azure portal](https://portal.azure.com) with your administrator account.
2. Navigate to the **Resource Groups** tab.
3. Select the **Resource Group** that you want to grant the VM's managed identity access.
4. In the left panel, select **Access control \(IAM\)**.
5. Select **Add**, then select **Add role assignment**.
6. In the **Role** tab, select **Reader**. This role allows view all resources, but doesn't allow you to make any changes.
7. In the **Members** tab, in the **Assign access to** option, select **Managed identity**, then select **+ Select members**.
8. Ensure the proper subscription is listed in the **Subscription** dropdown. For **Resource Group**, select **All resource groups**.
9. In the **Manage identity** dropdown, select **Virtual Machine**.
10. In the **Select** option, choose your VM in the dropdown, then select **Save**.

    ![Screenshot that shows adding the reader role to the managed identity.](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/msi-tutorial-linux-vm-access-arm/msi-permission-linux.png)

## Get an access token

Use the VM's system-assigned managed identity and call the resource manager to get an access token.

To complete these steps, you need an SSH client. If you're using Windows, you can use the SSH client in the [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/about). If you need assistance configuring your SSH client's keys, see [How to Use SSH keys with Windows on Azure](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/ssh-from-windows), or [How to create and use an SSH public and private key pair for Linux VMs in Azure](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/mac-create-ssh-keys).

1. In the Azure portal, navigate to your Linux VM.
2. In the **Overview**, select **Connect**.
3. **Connect** to the VM with the SSH client of your choice.
4. In the terminal window, using `curl`, make a request to the local managed identities for Azure resources endpoint to get an access token for Azure resource manager. The `curl` request for the access token is below.

```bash
curl 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https://management.azure.com/' -H Metadata:true
```

Note

The value of the `resource` parameter must be an exact match for what is expected by Microsoft Entra ID. In the case of the resource manager resource ID, you must include the trailing slash on the URI.

The response includes the access token you need to access Azure resource manager.

Response:

```json
{
  "access_token":"eyJ0eXAiOi...",
  "refresh_token":"",
  "expires_in":"3599",
  "expires_on":"1504130527",
  "not_before":"1504126627",
  "resource":"https://management.azure.com",
  "token_type":"Bearer"
}
```

Use this access token to access Azure resource manager. For example, to read the details of the resource group to which you previously granted this VM access. Replace the values of `<SUBSCRIPTION-ID>`, `<RESOURCE-GROUP>`, and `<ACCESS-TOKEN>` with the ones you created earlier.

Note

The URL is case-sensitive, so ensure if you are using the exact case as you used earlier when you named the resource group, and the uppercase “G” in `resourceGroup`.

```bash
curl https://management.azure.com/subscriptions/<SUBSCRIPTION-ID>/resourceGroups/<RESOURCE-GROUP>?api-version=2016-09-01 -H "Authorization: Bearer <ACCESS-TOKEN>" 
```

The response back with the specific resource group information:

```json
{
"id":"/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/resourceGroups/DevTest",
"name":"DevTest",
"location":"westus",
"properties":
{
  "provisioningState":"Succeeded"
  }
} 
```

## Next steps

In this quickstart, you learned how to use a system-assigned managed identity on a VM to access the Azure Resource Manager API. To learn more about Azure Resource Manager, see:

[Azure Resource Manager](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview) [Create, list or delete a user-assigned managed identity using Azure PowerShell](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-manage-user-assigned-managed-identities?pivots=identity-mi-methods-powershell)
