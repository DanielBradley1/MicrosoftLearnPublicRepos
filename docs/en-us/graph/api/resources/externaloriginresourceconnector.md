<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# externalOriginResourceConnector resource type

Namespace: microsoft.graph

Represents a connector used to communicate with an external resource system in Microsoft Entra ID Governance. The connector integrates with SAP Identity Access Governance \(SAP IAG\) to enable access management and governance for resources that originate in that system.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-externaloriginresourceconnectors?view=graph-rest-1.0) | [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) collection | Get a list of the [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-externaloriginresourceconnectors?view=graph-rest-1.0) | [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) | Create a new [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/externaloriginresourceconnector-get?view=graph-rest-1.0) | [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) | Read the properties and relationships of an [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/externaloriginresourceconnector-update?view=graph-rest-1.0) | [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) | Update the properties of an [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/externaloriginresourceconnector-delete?view=graph-rest-1.0) | None | Delete an [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| connectionInfo | [connectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-1.0) | The connection information used to communicate with the external resource system. When **connectorType** is `sapIag`, the type is [externalTokenBasedSapIagConnectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/externaltokenbasedsapiagconnectioninfo?view=graph-rest-1.0). |
| connectorType | connectorType | The type of connector to SAP being used. The possible values are: `sapIag` \(SAP Cloud Identity Access Governance\), `unknownFutureValue`. |
| createdBy | String | The identifier of the user or application that created the connector. |
| createdDateTime | DateTimeOffset | The date and time when the connector was created. |
| description | String | A description of the connector. |
| displayName | String | The display name of the connector. |
| id | String | The unique identifier of the connector. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| modifiedBy | String | The identifier of the user or application that last modified the connector. |
| modifiedDateTime | DateTimeOffset | The date and time when the connector was last modified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalOriginResourceConnector",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "connectorType": "String",
  "connectionInfo": {
    "@odata.type": "microsoft.graph.connectionInfo"
  },
  "createdBy": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedBy": "String",
  "modifiedDateTime": "String (timestamp)"
}
```
