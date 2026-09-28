<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-15 -->

# externalProfile resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines an external profile. This object is the base type for [externalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/externaluserprofile?view=graph-rest-beta) and [pendingExternalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/pendingexternaluserprofile?view=graph-rest-beta) resource types.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalOfficeAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicalofficeaddress?view=graph-rest-beta) | The office address of the external user profile. |
| companyName | String | The company name of the external user profile. Supports `$filter` \(`eq`, `startswith`\). |
| createdBy | String | The object ID of the user who created the external user profile. Read-only. Not nullable. |
| createdDateTime | DateTimeOffset | Date and time when this external user was created. Not nullable. Read-only. |
| deletedDateTime | DateTimeOffset | Date and time when this external user profile was deleted. Always `null` when the object isn't deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |
| department | String | The department of the external user profile. |
| displayName | String | The display name of the external user profile. |
| id | String | The unique identifier for the external user profile. Not nullable. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isDiscoverable | Boolean | Represents whether the external user profile is discoverable in the directory. When `true`, this external profile shows up in Teams search. |
| isEnabled | Boolean | Represents whether the external user profile is enabled in the directory. This property is peer to the `accountEnabled` property on the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) object. |
| jobTitle | String | The job title of the external user profile. |
| phoneNumber | String | The phone number of the external user profile. Must be in E164 format. |
| supervisorId | String | The object ID of the supervisor of the external user profile. Supports `$filter` \(`eq`, `startswith`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalProfile",
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
