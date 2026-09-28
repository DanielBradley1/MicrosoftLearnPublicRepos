<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# sharePointGroupIdentity resource type

Namespace: microsoft.graph

Represents the identity of a SharePoint group. Extends the [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) type with SharePoint-specific properties.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the SharePoint group. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). Read-only. |
| id | String | The unique identifier of the SharePoint group. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). Read-only. |
| principalId | String | The principal ID of the SharePoint group in the tenant. Read-only. |
| title | String | The title of the SharePoint group. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointGroupIdentity",
  "displayName": "String",
  "id": "String",
  "principalId": "String",
  "title": "String"
}
```

## Related content

- [sharePointIdentitySet resource type](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentityset?view=graph-rest-1.0)
- [identity resource type](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0)
- [sharePointGroup resource type](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0)
