<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumbermanagementroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# telephoneNumberManagementRoot resource type

Namespace: microsoft.graph.teamsAdministration

Represents a collection of available telephone number management operations.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List number assignments](https://learn.microsoft.com/en-us/graph/api/teamsadministration-telephonenumbermanagementroot-list-numberassignments?view=graph-rest-1.0) | [microsoft.graph.teamsAdministration.numberAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-numberassignment?view=graph-rest-1.0) collection | Get a list of the [numberAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-numberassignment?view=graph-rest-1.0) objects and their properties. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| numberAssignments | [microsoft.graph.teamsAdministration.numberAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-numberassignment?view=graph-rest-1.0) collection | Represents a collection of synchronous telephone number management operations. |
| operations | [microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumberlongrunningoperation?view=graph-rest-1.0) collection | Represents a collection of asynchronous telephone number management operations. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.telephoneNumberManagementRoot"
}
```
