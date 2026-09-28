<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobentitynameandidsfilter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-15 -->

# recoveryJobEntityNameAndIdsFilter resource type

Namespace: microsoft.graph.entraRecoveryServices

Filters a [recovery job](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0) to only include changes for specific entities identified by type and ID. Used as **filteringCriteria** in [Create recoveryPreviewJob](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-post-recoverypreviewjobs?view=graph-rest-1.0) and [Create recoveryJob](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-post-recoveryjobs?view=graph-rest-1.0) operations.

Inherits from [microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobfilteringcriteriabase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| filterValues | [microsoft.graph.entraRecoveryServices.entityTypeAndIds](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-entitytypeandids?view=graph-rest-1.0) collection | The list of entity type and ID pairs to include in the recovery job. Duplicate entity types are not allowed and return a `400 Bad Request` error. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJobEntityNameAndIdsFilter",
  "filterValues": [
    {
      "@odata.type": "microsoft.graph.entraRecoveryServices.entityTypeAndIds"
    }
  ]
}
```
