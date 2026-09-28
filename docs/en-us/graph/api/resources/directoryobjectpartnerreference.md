<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directoryobjectpartnerreference?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# directoryObjectPartnerReference resource type

Namespace: microsoft.graph

Represents a reference to a directory object in a partner organization. Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-v1.0&preserve-view=true).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of the object returned. Read-only. |
| displayName | String | Name of directory object being returned, like group or application. Read-only. |
| externalPartnerTenantId | Guid | The tenant identifier for the partner tenant. Read-only. |
| id | String | The unique identifier for the resource. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-v1.0&preserve-view=true). Read-only. |
| objectType | String | The type of the referenced object in the partner tenant. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String ",
  "displayName": "String",
  "externalPartnerTenantId": "String (identifier)",
  "id": "String (identifier)",
  "objectType": "String"
}
```

## Related content

- [Get directory objects from a list of ids](https://learn.microsoft.com/en-us/graph/api/directoryobject-getbyids?view=graph-rest-1.0)
