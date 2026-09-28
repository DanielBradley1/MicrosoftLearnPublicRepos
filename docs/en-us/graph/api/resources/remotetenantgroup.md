<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/remotetenantgroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# remoteTenantGroup resource type

Namespace: microsoft.graph

Represents a security group in a partner \(Managed Security Service Provider, or MSSP\) or governing tenant that administrators can discover from their own tenant. The calling tenant can target these groups when assigning workload permissions after delegated administrative privileges are set up via [Partner Center](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0).

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-remotetenantgroups?view=graph-rest-1.0) | [remoteTenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/remotetenantgroup?view=graph-rest-1.0) collection | Get a list of the remoteTenantGroup objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/remotetenantgroup-get?view=graph-rest-1.0) | [remoteTenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/remotetenantgroup?view=graph-rest-1.0) | Read the properties and relationships of a remoteTenantGroup object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object hasn't been deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| id | String | The unique identifier for the object. For example, `12345678-9abc-def0-1234-56789abcde`. The value of the **id** property is often but not exclusively in the form of a GUID; treat it as an opaque identifier and don't rely on it being a GUID. Key. Not nullable. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| remoteGroupDisplayName | String | Display name of the group in the remote tenant. |
| remoteGroupId | Guid | Unique identifier of the group in the remote tenant. |
| remoteTenantDisplayName | String | Display name of the remote tenant. |
| remoteTenantId | Guid | Unique identifier of the remote tenant. |
| remoteTenantPrimaryDomain | String | Primary domain name of the remote tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.remoteTenantGroup",
  "id": "String",
  "deletedDateTime": "DateTimeOffset",
  "remoteTenantId": "Guid",
  "remoteGroupId": "Guid",
  "remoteTenantDisplayName": "String",
  "remoteTenantPrimaryDomain": "String",
  "remoteGroupDisplayName": "String"
}
```
