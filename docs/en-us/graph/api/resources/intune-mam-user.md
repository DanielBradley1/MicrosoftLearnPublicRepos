<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# user resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an Azure Active Directory user object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List users](https://learn.microsoft.com/en-us/graph/api/intune-mam-user-list?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0) collection | List properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0) objects. |
| [Get user](https://learn.microsoft.com/en-us/graph/api/intune-mam-user-get?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0) | Read properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0) object. |
| [Create user](https://learn.microsoft.com/en-us/graph/api/intune-mam-user-create?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0) | Create a new [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0) object. |
| [Delete user](https://learn.microsoft.com/en-us/graph/api/intune-mam-user-delete?view=graph-rest-1.0) | None | Deletes a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0). |
| [Update user](https://learn.microsoft.com/en-us/graph/api/intune-mam-user-update?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0) | Update the properties of a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-user?view=graph-rest-1.0) object. |
| [getManagedAppDiagnosticStatuses function](https://learn.microsoft.com/en-us/graph/api/intune-mam-user-getmanagedappdiagnosticstatuses?view=graph-rest-1.0) | [managedAppDiagnosticStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdiagnosticstatus?view=graph-rest-1.0) collection | Gets diagnostics validation status for a given user. |
| [getManagedAppPolicies function](https://learn.microsoft.com/en-us/graph/api/intune-mam-user-getmanagedapppolicies?view=graph-rest-1.0) | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) collection | Gets app restrictions for a given user. |
| [wipeManagedAppRegistrationsByDeviceTag action](https://learn.microsoft.com/en-us/graph/api/intune-mam-user-wipemanagedappregistrationsbydevicetag?view=graph-rest-1.0) | None | Issues a wipe operation on an app registration with specified device tag. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The user identifier. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| managedAppRegistrations | [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) collection | Zero or more managed app registrations that belong to the user. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.user",
  "id": "String (identifier)"
}
```
