<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalsapacconnectioninfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# externalSapAcConnectionInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents connection information for connecting to SAP Access Control \(AC\) systems from Microsoft Entra Entitlement Management. This resource contains the configuration details required to establish a secure connection between an Entitlement Management [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-beta)'s **externalOriginResourceConnector** and an SAP AC system, including the target system identity and Azure Key Vault references for credential storage. Used when connectorType in [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-beta) is `sapAc`.

Inherits from [connectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationInfo | [authenticationInfo](https://learn.microsoft.com/en-us/graph/api/resources/authenticationinfo?view=graph-rest-beta) | The authentication configuration used to connect to the SAP AC system. |
| keyVaultName | String | The name of the Azure Key Vault that stores the credentials used for authentication. |
| resourceGroup | String | The Azure resource group that contains the Key Vault. |
| subscriptionId | String | The Azure subscription ID that contains the Key Vault. |
| systemId | String | The identifier of the target SAP AC system. |
| url | String | The endpoint that is used by Entitlement Management to communicate with the SAP AC system. Inherited from [connectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-beta). |
| userIdentifier | String | The user identifier used to connect to the SAP AC system. |

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
