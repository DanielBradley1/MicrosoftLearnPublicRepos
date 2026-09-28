<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/pendingexternaluserprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-16 -->

# pendingExternalUserProfile resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an external user profile in the Microsoft Entra tenant that hasn't consented to share data with the tenant.

Inherits from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/pendingexternaluserprofile-get?view=graph-rest-beta) | [pendingExternalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/pendingexternaluserprofile?view=graph-rest-beta) | Gets the properties of a pending external user profile. |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-pendingexternaluserprofile?view=graph-rest-beta) | [pendingExternalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/pendingexternaluserprofile?view=graph-rest-beta) collection | Gets a list of all pending external user profiles. |
| [Create](https://learn.microsoft.com/en-us/graph/api/directory-post-pendingexternaluserprofile?view=graph-rest-beta) | [pendingExternalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/pendingexternaluserprofile?view=graph-rest-beta) | Creates a new pending external user profile. |
| [Update](https://learn.microsoft.com/en-us/graph/api/pendingexternaluserprofile-update?view=graph-rest-beta) | None | Update a pending external user profile. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/directory-delete-pendingexternaluserprofiles?view=graph-rest-beta) | None | Delete a pending external user profile. |
| [List deleted items](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | Retrieve a list of recently deleted external user profiles from a collection of directory objects. |
| [Get deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | Retrieve the properties of a recently deleted external user profile object. |
| [Restore deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | Restore a recently deleted external user profile object. |
| [Permanently delete item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-beta) | None | Permanently delete an external user profile. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalOfficeAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicalofficeaddress?view=graph-rest-beta) | The office address of the pending external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| createdBy | String | The object ID of the user or principal who created the pending external user profile or invited the external user. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). Read-only. Not nullable. |
| createdDateTime | DateTimeOffset | Date and time when this pending external user profile was created. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). Not nullable. Read-only. |
| companyName | String | The company name of the pending external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). Supports the `$filter` \(`eq`, `startswith`\) query parameter. |
| deletedDateTime | DateTimeOffset | Date and time when the pending external user profile was deleted. Always `null` when the object isn't deleted. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| department | String | The department of the pending external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| displayName | String | The display name of the pending external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| id | String | The unique identifier for the pending external user profile. Not nullable. Read-only. |
| isDiscoverable | Boolean | Represents whether the pending external user profile is discoverable in the directory. When `true`, this external profile shows up in Teams search. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| isEnabled | Boolean | Represents whether the pending external user profile is enabled in the directory. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| jobTitle | String | The job title of the external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| phoneNumber | String | The phone number of the pending external user profile. Must be in E.164 format. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). |
| supervisorId | String | The object ID of the supervisor of the pending external user profile. Inherited from [externalProfile](https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta). Supports the `$filter` \(`eq`, `startswith`\) query parameter. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.pendingExternalUserProfile",
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
