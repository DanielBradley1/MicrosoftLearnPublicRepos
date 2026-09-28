<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceenvironment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# accessPackageResourceEnvironment resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package resource environment is a reference to the geolocation environment in which a resource is located. This environment is automatically provided as part of Microsoft Entra entitlement management. The API is only applicable to Multi-Geo SharePoint Online sites.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-resourceenvironments?view=graph-rest-1.0) | [accessPackageResourceEnvironment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceenvironment?view=graph-rest-1.0) collection | Retrieve a list of [accessPackageResourceEnvironment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceenvironment?view=graph-rest-1.0) objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| connectionInfo | [connectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-1.0) | Connection information of an environment used to connect to a resource. |
| createdDateTime | DateTimeOffset | The date and time that this object was created.  <br>The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | The description of this object. |
| displayName | String | The display name of this object. |
| id | String | The system-assigned unique identifier of the object. |
| isDefaultEnvironment | Boolean | Determines whether this is default environment or not. It is set to `true` for all static origin systems, such as Microsoft Entra groups and Microsoft Entra Applications. |
| modifiedDateTime | DateTimeOffset | The date and time that this object was last modified.  <br>The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| originId | String | The unique identifier of this environment in the origin system. |
| originSystem | String | The type of the resource in the origin system, that is, `SharePointOnline`. Requires `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| resources | [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) collection | Read-only. Required. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageResourceEnvironment",
  "id": "String (identifier)",
  "connectionInfo": {
    "@odata.type": "microsoft.graph.connectionInfo"
  },
  "displayName": "String",
  "description": "String",
  "originSystem": "String",
  "originId": "String",
  "isDefaultEnvironment": true,
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)"
}
```
