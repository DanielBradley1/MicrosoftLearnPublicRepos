<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# directoryObject resource type

Namespace: microsoft.graph

Represents a Microsoft Entra object. The **directoryObject** type is the base type for the following directory entity types generally referred to as directory objects:

- [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0)
- [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0)
- [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0)
- [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0)
- [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0)
- [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)
- [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0)
- [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0)
- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get directory object](https://learn.microsoft.com/en-us/graph/api/directoryobject-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Read the properties of a directory object. |
| [Get delta for directory object](https://learn.microsoft.com/en-us/graph/api/directoryobject-delta?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get incremental changes for directory objects such as [users](https://learn.microsoft.com/en-us/graph/api/user-delta?view=graph-rest-1.0), [groups](https://learn.microsoft.com/en-us/graph/api/group-delta?view=graph-rest-1.0), [applications](https://learn.microsoft.com/en-us/graph/api/application-delta?view=graph-rest-1.0), and [service principals](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delta?view=graph-rest-1.0). Filtering is required on either the **id** of the derived type or the derived type itself. For more information on delta queries, see the [Use delta query to track changes in Microsoft Graph data](https://learn.microsoft.com/en-us/graph/delta-query-overview). |
| [Delete directory object](https://learn.microsoft.com/en-us/graph/api/directoryobject-delete?view=graph-rest-1.0) | None | Delete a directory object. |
| [Get available extension properties](https://learn.microsoft.com/en-us/graph/api/directoryobject-getavailableextensionproperties?view=graph-rest-1.0) | [extensionProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty?view=graph-rest-1.0) collection | Get all or a filtered list of the directory extension properties that have been registered in a directory. |
| [Check member groups](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmembergroups?view=graph-rest-1.0) | String collection | Check for membership in a specified list of groups, and return from that list those groups of which the specified user, group, service principal, organizational contact, device, or directory object is a member. The check is transitive. |
| [Get member groups](https://learn.microsoft.com/en-us/graph/api/directoryobject-getmembergroups?view=graph-rest-1.0) | String collection | Return all groups that the user, group, service principal, organizational contact, device, or directory object is a member of. The check is transitive. |
| [Check member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmemberobjects?view=graph-rest-1.0) | String collection | Check for membership in a list of group, administrative units, or directory roles for the specified user, group, device, organizational contact, or directory object. This method is transitive. |
| [Get member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-getmemberobjects?view=graph-rest-1.0) | String collection | Return all groups, administrative units, and directory roles that the user, group, device, organizational contact, or directory object is a member of. The check is transitive. |
| [Get objects by IDs](https://learn.microsoft.com/en-us/graph/api/directoryobject-getbyids?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get a set of directory objects based on a set of supplied ids. |
| [Validate properties](https://learn.microsoft.com/en-us/graph/api/directoryobject-validateproperties?view=graph-rest-1.0) | JSON | Validate that a Microsoft 365 group's display name or mail nickname complies with naming policies. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object hasn't been deleted. |
| id | String | The unique identifier for the object. For example, `12345678-9abc-def0-1234-56789abcde`. The value of the **id** property is often but not exclusively in the form of a GUID; treat it as an opaque identifier and do not rely on it being a GUID. Key. Not nullable. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "deletedDateTime": "String (timestamp)",
  "id": "String (identifier)"
}
```
