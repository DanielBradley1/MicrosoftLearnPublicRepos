<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalsapacconnectioninfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-14 -->

# externalSapAcConnectionInfo resource type

Namespace: microsoft.graph

Represents connection information for connecting to SAP Access Control \(AC\) systems from Microsoft Entra Entitlement Management. This resource contains the configuration details required to establish a secure connection between an Entitlement Management [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0)'s **externalOriginResourceConnector** and an SAP AC system, including the target system identity and Azure Key Vault references for credential storage. The **connectionInfo** property of an [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) uses this type when **connectorType** is `sapAc`.

Inherits from [connectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationInfo | [authenticationInfo](https://learn.microsoft.com/en-us/graph/api/resources/authenticationinfo?view=graph-rest-1.0) | The authentication configuration used to connect to the SAP AC system. Use a concrete derived type, such as [clientCredentialAuthenticationInfo](https://learn.microsoft.com/en-us/graph/api/resources/clientcredentialauthenticationinfo?view=graph-rest-1.0). Not nullable. |
| keyVaultName | String | The name of the Azure Key Vault that stores the credentials used for authentication. Nullable. |
| resourceGroup | String | The Azure resource group that contains the Key Vault. Nullable. |
| subscriptionId | String | The Azure subscription ID that contains the Key Vault. Nullable. |
| systemId | String | The identifier of the target SAP AC system. Nullable. |
| url | String | The endpoint that is used by Entitlement Management to communicate with the SAP AC system. Inherited from [connectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-1.0). Nullable. |
| userIdentifier | String | The user identifier used to connect to the SAP AC system. Nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalSapAcConnectionInfo",
  "url": "String",
  "subscriptionId": "String",
  "resourceGroup": "String",
  "keyVaultName": "String",
  "systemId": "String",
  "userIdentifier": "String",
  "authenticationInfo": {
    "@odata.type": "microsoft.graph.authenticationInfo"
  }
}
```
