<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# unifiedGroupSource resource type

Namespace: microsoft.graph.security

The container for a custodian's group.

Inherits from [dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-list-unifiedgroupsources?view=graph-rest-1.0) | [microsoft.graph.security.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) collection | Get a list of the [unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) objects associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-post-unifiedgroupsources?view=graph-rest-1.0) | [microsoft.graph.security.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) | Create a new [unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-unifiedgroupsource-delete?view=graph-rest-1.0) | None | Delete a [unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the **unifiedGroupSource**. |
| createdDateTime | DateTimeOffset | The date and time the **unifiedGroupSource** was created. |
| displayName | String | The display name of the unified group, which is the name of the group. |
| holdStatus | microsoft.graph.security.dataSourceHoldStatus | The hold status of the **unifiedGroupSource**. The possible values are: `notApplied`, `applied`, `applying`, `removing`, `partial` |
| id | String | The ID of the **unifiedGroupSource**. This isn't the ID of the actual group. |
| includedSources | microsoft.graph.security.sourceType | Specifies which sources are included in this group. The possible values are: `mailbox`, `site`. |

### sourceType values

| Member | Description |
| :--- | --- |
| mailbox | Represents a mailbox. |
| site | Represents a SharePoint site. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Represents a group. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.unifiedGroupSource",
  "id": "String (identifier)",
  "displayName": "String",
  "holdStatus": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "includedSources": "String"
}
```
