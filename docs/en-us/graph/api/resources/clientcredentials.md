<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/clientcredentials?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# clientCredentials resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the information and properties of a [clientCredentials](https://learn.microsoft.com/en-us/graph/api/resources/clientcredentials?view=graph-rest-beta) object that is one of the prerequisites for administrators to call the Tenant Configuration Management application onboarding API. The **clientCredentials** includes the key-vault URI and certificate name that are generated during the creation of the Azure Key Vault.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateName | String | Name of the certificate that is uploaded by the admin in the Azure Key Vault. |
| keyVaultUri | String | The key-vault URI generated during the creation of the Azure Key Vault. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.clientCredentials",
  "certificateName": "String",
  "keyVaultUri": "String"
}
```
