<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# managedAppPolicy resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The ManagedAppPolicy resource represents a base type for platform specific policies.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAppPolicies](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapppolicy-list?view=graph-rest-1.0) | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) collection | List properties and relationships of the [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) objects. |
| [Get managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapppolicy-get?view=graph-rest-1.0) | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) | Read properties and relationships of the [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) object. |
| [targetApps action](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapppolicy-targetapps?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Policy display name. |
| description | String | The policy's description. |
| createdDateTime | DateTimeOffset | The date and time the policy was created. |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. |
| id | String | Key of the entity. |
| version | String | Version of the entity. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppPolicy",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "version": "String"
}
```
