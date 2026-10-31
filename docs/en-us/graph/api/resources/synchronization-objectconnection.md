<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectconnection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# objectConnection resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a connector data store linkage record for an object in a [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-beta).

Use this resource to inspect the cached linkage between a source object and its target identifier, or clear a stale linkage so the object is re-evaluated during a later synchronization cycle. Connections are created by the synchronization engine and their properties are read-only.

During public preview, collection listing isn't supported. Retrieve an individual connection using a known **objectId**. A GET request to the **objectConnections** collection returns `400 Bad Request`.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/synchronization-objectconnection-get?view=graph-rest-beta) | [objectConnection](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectconnection?view=graph-rest-beta) | Get the cached linkage record for a known object in a synchronization job. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-delete-objectconnections?view=graph-rest-beta) | None | Clear the cached linkage record for an object in a synchronization job. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the connected object. Nullable. Read-only. |
| objectId | String | Identifier supplied in the request to look up the connection. Can be the source or target identifier for the object in the synchronization job. Key. Not nullable. Read-only. |
| objectTypeName | String | Logical object type, such as `User` or `Group`. Not nullable. Read-only. |
| sourceAnchor | String | Anchor or join value in the source directory. Not nullable. Read-only. |
| targetAnchor | String | Anchor or transformed identifier in the target space. Not nullable. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.objectConnection",
  "objectId": "String (identifier)",
  "sourceAnchor": "String",
  "targetAnchor": "String",
  "displayName": "String",
  "objectTypeName": "String"
}
```

## Related content

- [Manage provisioning object connections using Microsoft Graph](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/manage-object-connections)
