<!-- Source: https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/federatedidentitycredentials -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# applications/federatedIdentityCredentials

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Permissions for personal Microsoft accounts cannot be used to deploy Microsoft Graph resources declared in Terraform files.

### Resource deployment

Choose the least privileged permission from the following table to create or update a `applications/federatedIdentityCredentials` resource.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Application.ReadWrite.All | Not available. |
| Application | Application.ReadWrite.OwnedBy | Application.ReadWrite.All |

### Read existing resources only

Choose the least privileged permission from the following table to read a `applications/federatedIdentityCredentials` resource using the `msgraph_resource` data source.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Application.ReadWrite.All | Not available. |
| Application | Application.ReadWrite.OwnedBy | Application.ReadWrite.All |

## Resource format

To create a `applications/federatedIdentityCredentials` resource, add the following Terraform configuration to your Terraform configuration.

```terraform
resource "msgraph_resource" "symbolicname" {
  url = "applications/federatedIdentityCredentials@beta"
  body = {
    uniqueName = "string"

    resource childSymbolicname 'federatedIdentityCredentials@beta' = {
      audiences = [
        "string"
      ]
      description = "string"
      id = "string"
      issuer = "string"
      name = "string"
      subject = "string"
    }
  }
}
```

## Property values

### applications/federatedIdentityCredentials

| Name | Description | Value |
| --- | --- | --- |
| apiVersion | The resource api version | 'beta' \(ReadOnly\) |
| audiences | The audience that can appear in the external token. This field is mandatory and should be set to api://AzureADTokenExchange for Microsoft Entra ID. It says what Microsoft identity platform should accept in the aud claim in the incoming token. This value represents Microsoft Entra ID in your external identity provider and has no fixed value across identity providers - you might need to create a new application registration in your identity provider to serve as the audience of this token. This field can only accept a single value and has a limit of 600 characters. Required. | string\[\] |
| description | The unvalidated description of the federated identity credential, provided by the user. It has a limit of 600 characters. Optional. | string |
| id | The unique identifier for an entity. Read-only. | string |
| issuer | The URL of the external identity provider, which must match the issuer claim of the external token being exchanged. The combination of the values of issuer and subject must be unique within the app. It has a limit of 600 characters. Required. | string |
| name | The unique identifier for the federated identity credential, which has a limit of 120 characters and must be URL friendly. The string is immutable after it's created. Alternate key. Required. Not nullable. | string \(Required\) |
| subject | Required. The identifier of the external software workload within the external identity provider. Like the audience value, it has no fixed format; each identity provider uses their own - sometimes a GUID, sometimes a colon delimited identifier, sometimes arbitrary strings. The value here must match the sub claim within the token presented to Microsoft Entra ID. The combination of issuer and subject must be unique within the app. It has a limit of 600 characters. | string |
| type | The resource type | 'Microsoft.Graph/applications/federatedIdentityCredentials' \(ReadOnly\) |
