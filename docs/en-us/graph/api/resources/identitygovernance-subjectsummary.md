<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# subjectSummary resource type

Namespace: microsoft.graph.identityGovernance

A summary of subject processing results for a specified time period. This summary allows the administrator to get a quick overview based on counts. It's returned by the [summary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-subjectprocessingresult-summary?view=graph-rest-1.0) function on a collection of [subjectProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-1.0) objects.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedSubjects | Int32 | The number of subjects with at least one failed task in a subject summary. |
| failedTasks | Int32 | The number of failed tasks for subjects in a subject summary. |
| successfulSubjects | Int32 | The number of subjects where all tasks succeeded in a subject summary. |
| totalSubjects | Int32 | The total number of subjects in a subject summary. |
| totalTasks | Int32 | The total tasks of subjects in a subject summary. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.subjectSummary",
  "failedSubjects": "Integer",
  "failedTasks": "Integer",
  "successfulSubjects": "Integer",
  "totalSubjects": "Integer",
  "totalTasks": "Integer"
}
```
