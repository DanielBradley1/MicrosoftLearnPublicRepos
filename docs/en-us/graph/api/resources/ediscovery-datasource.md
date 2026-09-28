<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# dataSource resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

The dataSource entity is an abstract base class used to identify sources of content for eDiscovery.

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who created the **dataSource**. |
| createdDateTime | DateTimeOffset | The date and time the **dataSource** was created. |
| displayName | String | The display name of the **dataSource**, and is the name of the SharePoint site. |
| id | String | The ID of the **dataSource**. This isn't the ID of the actual site. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.dataSource",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "id": "String (identifier)"
}
```
