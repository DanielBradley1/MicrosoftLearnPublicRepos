<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-22 -->

# dataSource resource type

Namespace: microsoft.graph.security

An abstract base class used to identify the following sources of content for eDiscovery.

- [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0)
- [unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0)
- [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the **dataSource**. |
| createdDateTime | DateTimeOffset | The date and time the **dataSource** was created. |
| displayName | String | The display name of the **dataSource** and is the name of the SharePoint site. |
| holdStatus | microsoft.graph.security.dataSourceHoldStatus | The hold status of the **dataSource**. The possible values are: `notApplied`, `applied`, `applying`, `removing`, `partial`. |
| id | String | The ID of the **dataSource** and isn't the ID of the actual site. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.dataSource",
  "id": "String (identifier)",
  "displayName": "String",
  "holdStatus": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```
