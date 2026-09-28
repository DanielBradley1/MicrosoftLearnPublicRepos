<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasourcecontainer?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# dataSourceContainer resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Base class for [custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) and [noncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Created date and time of the dataSourceContainer entity. |
| displayName | String | Display name of the dataSourceContainer entity. |
| id | String | Unique identifier of the dataSourceContainer. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last modified date and time of the dataSourceContainer. |
| releasedDateTime | DateTimeOffset | Date and time that the dataSourceContainer was released from the case. |
| status | microsoft.graph.ediscovery.dataSourceContainerStatus | Latest status of the dataSourceContainer. The possible values are: `Active`, `Released`. |

### dataSourceContainerStatus values

| Member | Description |
| :--- | :--- |
| Active | The dataSourceContainer is on hold in the case. |
| Released | The dataSourceContainer was released from hold in the case. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.dataSourceContainer",
  "id": "String (identifier)",
  "status": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "releasedDateTime": "String (timestamp)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)"
}
```
