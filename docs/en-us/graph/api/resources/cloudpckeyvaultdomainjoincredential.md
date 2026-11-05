<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpckeyvaultdomainjoincredential?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# cloudPcKeyVaultDomainJoinCredential resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an Active Directory domain join credential whose password is stored in a customer-owned Azure Key Vault.

Inherits from [cloudPcDomainJoinCredential](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoincredential?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| keyVaultIntentConfiguration | [cloudPcDomainJoinKeyVaultIntentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoinkeyvaultintentconfiguration?view=graph-rest-beta) | The configuration that specifies how the Azure Key Vault secret is used as the Active Directory domain join credential. Set **@odata.type** to `#microsoft.graph.cloudPcDomainJoinKeyVaultPasswordConfiguration` to indicate that the secret contains the password. Required. |
| keyVaultResourceId | String | The full Azure Resource Manager resource ID of the Azure Key Vault that stores the domain join password. Required format: `/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}/providers/Microsoft.KeyVault/vaults/{vaultName}`. Required. |
| secretName | String | The name of the secret in the Azure Key Vault that stores the domain join password. Required. |
| serviceConnectorResourceId | String | The full Azure Resource Manager resource ID of the Windows 365 service connector that grants Windows 365 access to the Azure Key Vault. Required format when specified: `/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}/providers/Microsoft.Windows365/serviceConnectors/{serviceConnectorName}`. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcKeyVaultDomainJoinCredential",
  "keyVaultIntentConfiguration": { "@odata.type": "microsoft.graph.cloudPcDomainJoinKeyVaultIntentConfiguration" },
  "keyVaultResourceId": "String",
  "secretName": "String",
  "serviceConnectorResourceId": "String"
}
```
