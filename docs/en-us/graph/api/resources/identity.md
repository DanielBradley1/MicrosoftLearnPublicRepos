<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-18 -->

# identity resource type \(actor\)

Namespace: microsoft.graph

Represents an identity of an *actor*. For example, an actor can be a user, device, or application. Multiple Microsoft Graph APIs share this resource and the data they return varies depending on the API.

Base type of [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identity.  <br>  <br>For drive items, the display name might not always be available or up to date. For example, if a user changes their display name the API might show the new value in a future response, but the items associated with the user don't show up as changed when using [delta](https://learn.microsoft.com/en-us/graph/api/driveitem-delta?view=graph-rest-1.0). |
| id | String | Unique identifier for the identity or actor. For example, in the access reviews decisions API, this property might record the **id** of the principal, that is, the group, user, or application that's subject to review. |
| tenantId | String | Unique identity of the tenant. Optional. |
| thumbnails | [thumbnailSet](https://learn.microsoft.com/en-us/graph/api/resources/thumbnailset?view=graph-rest-1.0) | Keyed collection of thumbnail resources. Optional. Applies to drive items, for example. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)",
  "tenantId": "String",
  "thumbnails": { "@odata.type": "microsoft.graph.thumbnailSet" }
}
```
