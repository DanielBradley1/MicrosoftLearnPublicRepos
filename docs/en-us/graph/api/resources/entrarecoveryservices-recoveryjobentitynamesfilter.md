<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobentitynamesfilter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-15 -->

# recoveryJobEntityNamesFilter resource type

Namespace: microsoft.graph.entraRecoveryServices

Filters a [recovery job](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0) to only include changes for specified entity types \(for example, only users, or only users and groups\). Used as **filteringCriteria** in [Create recoveryPreviewJob](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-post-recoverypreviewjobs?view=graph-rest-1.0) and [Create recoveryJob](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-post-recoveryjobs?view=graph-rest-1.0) operations.

Inherits from [microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobfilteringcriteriabase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| entityTypes | [microsoft.graph.entraRecoveryServices.resourceTypeName](https://learn.microsoft.com/en-us/graph/api/resources/enums-entrarecoveryservices?view=graph-rest-1.0) collection | The list of entity types to include in the recovery job. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJobEntityNamesFilter",
  "entityTypes": [
    "String"
  ]
}
```
