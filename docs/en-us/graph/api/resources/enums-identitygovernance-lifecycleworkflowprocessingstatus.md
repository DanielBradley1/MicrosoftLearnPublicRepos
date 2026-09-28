<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance-lifecycleworkflowprocessingstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# lifecycleWorkflowProcessingStatus enum type

Namespace: microsoft.graph.identityGovernance

Describes the execution status of a lifecycle workflow. This enum is used by the **processingStatus** property of the following resources:

- [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0)
- [task processing result](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0)
- [task report](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreport?view=graph-rest-1.0)
- [user processing result](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0)

## lifecycleWorkflowProcessingStatus values

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). You must use the `Prefer: include-unknown-enum-members` request header to get the following values in this evolvable enum: `canceling`, `quarantined`.

| Member |
| :--- |
| queued |
| inProgress |
| completed |
| completedWithErrors |
| canceled |
| failed |
| unknownFutureValue |
| canceling |
| quarantined |
