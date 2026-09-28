<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externaltokenbasedsapiagconnectioninfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# externalTokenBasedSapIagConnectionInfo resource type

Namespace: microsoft.graph

Represents connection information for token-based authentication to SAP Identity Access Governance \(SAP IAG\) systems. This resource contains the configuration details required to establish a secure connection between an Entitlement Management [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0)'s **externalOriginResourceConnector** and SAP IAG, including token endpoint information and Azure Key Vault references for credential storage. This type is used when the **connectorType** of the [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) is `sapIag`.

Inherits from [connectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessTokenUrl | String | The URL endpoint used to obtain access tokens for authentication with the SAP IAG system. |
| clientId | String | The client identifier used for authentication with the SAP IAG system. |
| keyVaultName | String | The name of the Azure Key Vault that stores the client secret for authentication. |
| resourceGroup | String | The Azure resource group that contains the Key Vault. |
| secretName | String | The name of the secret in Azure Key Vault that contains the client secret. |
| subscriptionId | String | The Azure subscription ID that contains the Key Vault. |
| url | String | The endpoint that is used by Entitlement Management to communicate with the SAP IAG system. Inherited from [connectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalTokenBasedSapIagConnectionInfo",
  "url": "String",
  "accessTokenUrl": "String",
  "clientId": "String",
  "keyVaultName": "String",
  "secretName": "String",
  "subscriptionId": "String",
  "resourceGroup": "String"
}
```
