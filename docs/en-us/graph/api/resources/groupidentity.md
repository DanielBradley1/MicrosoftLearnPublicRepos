<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groupidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# groupIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the identity of a group-connected site. This resource is an open type that allows additional properties beyond those documented here.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identity. For drive items, the display name might not always be available or up to date. For example, if a user changes their display name the API might show the new value in a future response, but the items associated with the user don't show up as changed when using [delta](https://learn.microsoft.com/en-us/graph/api/driveitem-delta?view=graph-rest-beta). Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta). |
| id | String | Unique identifier for the identity. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta). |
| mailNickname | String | The mail nick name, also known as group alias of the group-connected site. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.groupIdentity",
  "displayName": "String",
  "id": "String",
  "mailNickname": "String"
}
```
