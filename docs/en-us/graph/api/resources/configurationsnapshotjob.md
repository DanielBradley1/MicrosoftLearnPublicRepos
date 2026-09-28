<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# configurationSnapshotJob resource type

Namespace: microsoft.graph

Represents an asynchronous job that is created when an admin creates a snapshot. When an admin calls the [configurationBaseline: createSnapshot](https://learn.microsoft.com/en-us/graph/api/configurationbaseline-createsnapshot?view=graph-rest-1.0) API, a [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) is created and runs asynchronously. Once the job completes successfully, the admin can download the extraction.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create snapshot](https://learn.microsoft.com/en-us/graph/api/configurationbaseline-createsnapshot?view=graph-rest-1.0) | [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) | Create a [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) asynchronously. |
| [List snapshot jobs](https://learn.microsoft.com/en-us/graph/api/configurationmanagement-list-configurationsnapshotjobs?view=graph-rest-1.0) | [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) collection | Get a list of the [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) objects and their properties. |
| [Get snapshot job](https://learn.microsoft.com/en-us/graph/api/configurationsnapshotjob-get?view=graph-rest-1.0) | [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) | Read the properties and relationships of a [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) object. |
| [Delete snapshot job](https://learn.microsoft.com/en-us/graph/api/configurationsnapshotjob-delete?view=graph-rest-1.0) | None | Delete a [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | The date and time when the snapshot job was completed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `ge`, `le`\) and `$orderby`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user, app, or device that triggered the snapshot.  <br>  <br>Requires `$select` to retrieve. Supports `$filter` \(`eq`\). |
| createdDateTime | DateTimeOffset | The date and time when the snapshot job was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `ge`, `le`\) and `$orderby`. |
| description | String | User-friendly description of the snapshot given by the user.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `startsWith`\) and `$orderby`. |
| displayName | String | User-friendly name provided by the user during snapshot creation.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `startsWith`\) and `$orderby`. |
| errorDetails | String collection | Details of errors related to the reasons why the snapshot can't complete.  <br>  <br>Requires `$select` to retrieve. |
| id | String | Globally unique identifier \(GUID\) of the snapshot job. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderby`. |
| resourceLocation | String | The URL at which the snapshot file resides.  <br>  <br>Requires `$select` to retrieve. |
| resources | String collection | The names of all resources included in the request body by the user who created the snapshot. Fetched by the system.  <br>  <br>Requires `$select` to retrieve. |
| status | snapshotJobStatus | Status of the snapshot. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`, `partiallySuccessful`. Use the `Prefer: include-unknown-enum-members` request header to get the following value in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `partiallySuccessful`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderby`. |
| tenantId | String | Globally unique identifier \(GUID\) of the tenant for which the snapshot is created.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.configurationSnapshotJob",
  "completedDateTime": "String (timestamp)",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "errorDetails": ["String"],
  "id": "String (identifier)",
  "resourceLocation": "String",
  "resources": ["String"],
  "status": "String",
  "tenantId": "String"
}
```
