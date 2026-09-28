<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/inboundshareduserprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# inboundSharedUserProfile resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Entra user from an external Microsoft Entra tenant whose profile data is shared with the current tenant using B2B direct connect.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/inboundshareduserprofile-get?view=graph-rest-beta) | [inboundSharedUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/inboundshareduserprofile?view=graph-rest-beta) | Read the properties of an inboundSharedUserProfile. |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-inboundshareduserprofiles?view=graph-rest-beta) | [inboundSharedUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/inboundshareduserprofile?view=graph-rest-beta) collection | Retrieve all inboundSharedUserProfiles in the directory. |
| [Remove personal data](https://learn.microsoft.com/en-us/graph/api/inboundshareduserprofile-removepersonaldata?view=graph-rest-beta) | None | Create a request to remove all personal data associated with the inboundSharedUserProfile from the directory. |
| [Export personal data](https://learn.microsoft.com/en-us/graph/api/inboundshareduserprofile-exportpersonaldata?view=graph-rest-beta) | None | Create a request to export all personal data associated with the inboundSharedUserProfile and stores it in the specified location. The storage location must be an Azure Storage Account. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name displayed in the address book for the user at the time when the sharing record was created. Read-only. |
| homeTenantId | String | The home tenant id of the external user. Read-only. |
| userId | String | The object id of the external user. Read-only. |
| userPrincipalName | String | The user principal name \(UPN\) of the external user. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.inboundSharedUserProfile",
  "userId": "String",
  "userPrincipalName": "String",
  "displayName": "String",
  "homeTenantId": "String"
}
```
