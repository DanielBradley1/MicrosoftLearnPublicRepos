<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restoresessionartifactcount?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# restoreSessionArtifactCount resource type

Namespace: microsoft.graph

Represents artifact count metadata for a [restore session](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0). Restore session APIs are used by SharePoint, OneDrive, and Exchange Online admins to perform restore-related tasks on artifacts that are protected as part of a protection policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| total | Int32 | The number of artifacts present in the restore session. |
| inProgress | Int32 | The number of artifacts whose restoration is in progress. |
| completed | Int32 | The number of artifacts whose restoration completed. |
| failed | Int32 | The number of artifacts whose restoration failed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restoreSessionArtifactCount",
  "total": "Int32",
  "inProgress": "Int32",
  "completed": "Int32",
  "failed": "Int32"
}
```
