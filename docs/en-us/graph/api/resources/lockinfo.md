<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/lockinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# lockInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **lockInfo** resource provides read-only lock metadata for a file. It indicates whether a file is locked, the kind of lock that is held, when the lock was created, when it expires, and which users currently hold the lock.

It is available on the **lockInfo** property of the [file](https://learn.microsoft.com/en-us/graph/api/resources/file?view=graph-rest-beta) facet on a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the lock was created, in UTC. Read-only. |
| expirationDateTime | DateTimeOffset | The date and time when the lock expires, in UTC. Read-only. |
| lockType | [lockType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#locktype-values) | The type of lock currently held on the file. The possible values are: `none`, `exclusive`, `shared`, `unknownFutureValue`. Read-only. |
| owners | Collection\([userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta)\) | The collection of users that currently hold the lock on the file. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.lockInfo",
  "lockType": "String",
  "createdDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "owners": [
    { "@odata.type": "microsoft.graph.userIdentity" }
  ]
}
```

## Remarks

For more information about the facets on a **driveItem**, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-beta).
