<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperationtype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-16 -->

# teamsAsyncOperationType enum type

Namespace: microsoft.graph

Types of [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0). Members are added as more async operations are supported. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `teamifyGroup`, `createChannel`, `archiveChannel`, `unarchiveChannel`.

## Members

| Member | Description |
| :--- | :--- |
| invalid | Invalid value. |
| cloneTeam | Operation to clone a team. |
| archiveTeam | Operation to archive a team. |
| unarchiveTeam | Operation to restore an archived team. |
| createTeam | Operation to create a team from scratch. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| teamifyGroup | Operation to create a team from a group. |
| createChannel | Operation to create a channel in a team. |
| archiveChannel | Operation to archive a channel. |
| unarchiveChannel | Operation to unarchive a channel. |
