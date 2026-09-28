<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/outboundshareduserprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# outboundSharedUserProfile resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Entra user that shared their profile data with an external Microsoft Entra tenant using B2B direct connect.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-outboundshareduserprofiles?view=graph-rest-beta) | [outboundSharedUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/outboundshareduserprofile?view=graph-rest-beta) collection | Retrieve all outboundSharedUserProfiles in the directory. |
| [Get](https://learn.microsoft.com/en-us/graph/api/outboundshareduserprofile-get?view=graph-rest-beta) | [outboundSharedUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/outboundshareduserprofile?view=graph-rest-beta) collection | Retrieve a specific outboundSharedUserProfile from the directory. |
| [List tenant references](https://learn.microsoft.com/en-us/graph/api/outboundshareduserprofile-list-tenants?view=graph-rest-beta) | [tenantReferences](https://learn.microsoft.com/en-us/graph/api/resources/tenantreference?view=graph-rest-beta) collection | Get all Microsoft Entra tenants that a user shared their data with as a Microsoft Entra B2B direct connect user. |
| [Remove personal data](https://learn.microsoft.com/en-us/graph/api/tenantreference-removepersonaldata?view=graph-rest-beta) | None | Create a request to remove all personal data associated with a remote user in an external Microsoft Entra tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userId | String | The object id of the external user. Read-only. |

## Relationships

| Property | Type | Description |
| :--- | :--- | :--- |
| tenants | [tenantReference](https://learn.microsoft.com/en-us/graph/api/resources/tenantreference?view=graph-rest-beta) collection | The collection of external Microsoft Entra tenants that the user shared profile data with. Read-only. |

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.outboundSharedUserProfile",
  "userId": "String"
}
```
