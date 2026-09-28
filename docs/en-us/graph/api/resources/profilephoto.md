<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/profilephoto?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# profilePhoto resource type

Namespace: microsoft.graph

Represents a profile photo of a user, group, team, or Outlook contact accessed from Exchange Online or Microsoft Entra ID. The data is binary and not encoded in base-64.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get team photo](https://learn.microsoft.com/en-us/graph/api/profilephoto-get?view=graph-rest-1.0) | [profilePhoto](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto?view=graph-rest-1.0) | Read the properties and relationships of a profile photo object. |
| [Update team photo](https://learn.microsoft.com/en-us/graph/api/profilephoto-update?view=graph-rest-1.0) | [profilePhoto](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto?view=graph-rest-1.0) | Update the properties of a profile photo object. |
| [Delete photo](https://learn.microsoft.com/en-us/graph/api/profilephoto-delete?view=graph-rest-1.0) | [profilePhoto](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto?view=graph-rest-1.0) | Delete the profile photo *of a user or group*. |

Note

- Managing users' photos using the Microsoft Graph API is currently *not supported in Azure AD B2C tenants*.
- The delete operation supports only user or group photos, but *not Outlook contact nor Teams photos*.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | Read-only. |
| height | int32 | The height of the photo. Read-only. |
| width | int32 | The width of the photo. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String",
  "height": 240,
  "width": 240
}
```
