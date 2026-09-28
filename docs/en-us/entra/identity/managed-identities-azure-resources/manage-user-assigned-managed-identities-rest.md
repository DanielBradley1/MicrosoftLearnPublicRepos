<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/manage-user-assigned-managed-identities-rest -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# Manage user-assigned managed identities using REST

Managed identities for Azure resources eliminate the need to manage credentials in code. You can use them to get a Microsoft Entra token for your applications. The applications can use the token when accessing resources that support Microsoft Entra authentication. Azure manages the identity so you don't have to.

There are two types of managed identities: system-assigned and user-assigned. System-assigned managed identities have their lifecycle tied to the resource that created them. This identity is restricted to only one resource, and you can grant permissions to the managed identity by using Azure role-based access control \(RBAC\). User-assigned managed identities can be used on multiple resources.

In this article, you learn how to create, list, and delete a user-assigned managed identity by using REST.

## Prerequisites

- If you're unfamiliar with managed identities for Azure resources, check out the [overview section](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview). *Be sure to review the [difference between a system-assigned and user-assigned managed identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview#managed-identity-types)*.
- If you don't already have an Azure account, [sign up for a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you continue.
- You can run all the commands in this article either in the cloud or locally:

  - To run in the cloud, use [Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview).
  - To run locally, install [curl](https://curl.se/download.html) and the [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli).

## Obtain a bearer access token

1. If you're running locally, sign in to Azure through the Azure CLI.

   ```azurecli
   az login
   ```

2. Obtain an access token by using [az account get-access-token](https://learn.microsoft.com/en-us/cli/azure/account#az-account-get-access-token).

   ```azurecli
   az account get-access-token
   ```

## Create a user-assigned managed identity

To create a user-assigned managed identity, your account needs the [Managed Identity Contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#managed-identity-contributor) role assignment.

Important

When you create user-assigned managed identities, the name must start with a letter or number, and may include a combination of alphanumeric characters, hyphens \(-\) and underscores \(\_\). For the assignment to a virtual machine or virtual machine scale set to work properly, the name is limited to 24 characters. For more information, see [FAQs and known issues](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/known-issues).

```bash
curl 'https://management.azure.com/subscriptions/<SUBSCRIPTION ID>/resourceGroup
s/<RESOURCE GROUP>/providers/Microsoft.ManagedIdentity/userAssignedIdentities/<USER ASSIGNED IDENTITY NAME>?api-version=2015-08-31-preview' -X PUT -d '{"location": "<LOCATION>"}' -H "Content-Type: application/json" -H "Authorization: Bearer <ACCESS TOKEN>"
```

```HTTP
PUT https://management.azure.com/subscriptions/<SUBSCRIPTION ID>/resourceGroup
s/<RESOURCE GROUP>/providers/Microsoft.ManagedIdentity/userAssignedIdentities/<USER ASSIGNED IDENTITY NAME>?api-version=2015-08-31-preview HTTP/1.1
```

**Request headers**

| Request header | Description |
| --- | --- |
| *Content-Type* | Required. Set to `application/json`. |
| *Authorization* | Required. Set to a valid `Bearer` access token. |

**Request body**

| Name | Description |
| --- | --- |
| Location | Required. Resource location. |

## List user-assigned managed identities

To list or read a user-assigned managed identity, your account needs the [Managed Identity Operator](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#managed-identity-operator) or [Managed Identity Contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#managed-identity-contributor) role assignment.

```bash
curl 'https://management.azure.com/subscriptions/<SUBSCRIPTION ID>/resourceGroups/<RESOURCE GROUP>/providers/Microsoft.ManagedIdentity/userAssignedIdentities?api-version=2015-08-31-preview' -H "Authorization: Bearer <ACCESS TOKEN>"
```

```HTTP
GET https://management.azure.com/subscriptions/<SUBSCRIPTION ID>/resourceGroups/<RESOURCE GROUP>/providers/Microsoft.ManagedIdentity/userAssignedIdentities?api-version=2015-08-31-preview HTTP/1.1
```

| Request header | Description |
| --- | --- |
| *Content-Type* | Required. Set to `application/json`. |
| *Authorization* | Required. Set to a valid `Bearer` access token. |

## Delete a user-assigned managed identity

To delete a user-assigned managed identity, your account needs the [Managed Identity Contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#managed-identity-contributor) role assignment.

Deleting a user-assigned managed identity won't remove the reference from any resource it was assigned to.

```bash
curl 'https://management.azure.com/subscriptions/<SUBSCRIPTION ID>/resourceGroup
s/<RESOURCE GROUP>/providers/Microsoft.ManagedIdentity/userAssignedIdentities/<USER ASSIGNED IDENTITY NAME>?api-version=2015-08-31-preview' -X DELETE -H "Authorization: Bearer <ACCESS TOKEN>"
```

```HTTP
DELETE https://management.azure.com/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/resourceGroups/TestRG/providers/Microsoft.ManagedIdentity/userAssignedIdentities/<USER ASSIGNED IDENTITY NAME>?api-version=2015-08-31-preview HTTP/1.1
```

| Request header | Description |
| --- | --- |
| *Content-Type* | Required. Set to `application/json`. |
| *Authorization* | Required. Set to a valid `Bearer` access token. |
