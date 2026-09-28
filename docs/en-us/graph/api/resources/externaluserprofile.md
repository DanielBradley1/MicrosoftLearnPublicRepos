<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externaluserprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-16 -->

# externalUserProfile resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the profile of an external user in a Microsoft Entra tenant. This profile is created when a user redeems their [pendingExternalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/pendingexternaluserprofile?view=graph-rest-beta). The pending external user profile can be created through the [Create pendingExternalUserProfile](https://learn.microsoft.com/en-us/graph/api/directory-post-pendingexternaluserprofile?view=graph-rest-beta) API.

Inherits from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/externaluserprofile-get?view=graph-rest-beta) | [externalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/externaluserprofile?view=graph-rest-beta) | Gets the properties of an external user profile. |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-externaluserprofiles?view=graph-rest-beta) | [externalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/externaluserprofile?view=graph-rest-beta) collection | Gets a list of all external user profiles. |
| [Update](https://learn.microsoft.com/en-us/graph/api/externaluserprofile-update?view=graph-rest-beta) | None | Update an external user profile. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/directory-delete-externaluserprofiles?view=graph-rest-beta) | None | Delete an external user profile. |
| [List deleted items](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | Retrieve a list of recently deleted external user profiles from a collection of directory objects. |
| [Get deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | Retrieve the properties of a recently deleted external user profile object. |
| [Restore deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | Restore a recently deleted external user profile object. |
| [Permanently delete item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-beta) | None | Permanently delete an external user profile. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalOfficeAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicalofficeaddress?view=graph-rest-beta) | The office address of the external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| createdBy | String | The object ID of the user who created the external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). Read-only. Not nullable. |
| createdDateTime | DateTimeOffset | Date and time when this external user was created. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). Not nullable. Read-only. |
| companyName | String | The company name of the external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). Supports `$filter` \(`eq`, `startswith`\). |
| deletedDateTime | DateTimeOffset | Date and time when this external user profile was deleted. Always `null` when the object isn't deleted. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| department | String | The department of the external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| displayName | String | The display name of the external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| id | String | The unique identifier for the external user profile. For example, 12345678-9abc-def0-1234-56789abcde. The value of the **id** property is often but not exclusively in the form of a GUID; treat it as an opaque identifier and don't rely on it being a GUID. Key. Not nullable. Read-only. |
| isDiscoverable | Boolean | Represents whether the external user profile is discoverable in the directory. When `true`, this external profile shows up in Teams search. When `false`, this external profile doesn't show up in Teams search. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| isEnabled | Boolean | Represents whether the external user profile is enabled in the directory. This property is peer to the `accountEnabled` property on the [User](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) object. |
| jobTitle | String | The job title of the external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| phoneNumber | String | The phone number of the external user profile. Must be in E164 format. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| supervisorId | String | The object ID of the supervisor of the external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). Supports `$filter` \(`eq`, `startswith`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalUserProfile",
  "id": "String (identifier)",
  "deletedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "companyName": "String",
  "displayName": "String",
  "jobTitle": "String",
  "isDiscoverable": "Boolean",
  "isEnabled": "Boolean",
  "department": "String",
  "phoneNumber": "String",
  "address": {
    "@odata.type": "microsoft.graph.physicalOfficeAddress"
  },
  "supervisorId": "String"
}
```
