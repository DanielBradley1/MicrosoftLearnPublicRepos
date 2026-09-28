<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsadminroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# teamsAdminRoot resource type

Namespace: microsoft.graph.teamsAdministration

Represents a collection of user configurations and telephone number administration methods.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [microsoft.graph.teamsAdministration.teamsPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamspolicyassignment?view=graph-rest-1.0) | Represents a navigation property to the Teams policy assignment object. |
| userConfigurations | [microsoft.graph.teamsAdministration.teamsUserConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsuserconfiguration?view=graph-rest-1.0) collection | Represents the configuration information of users who have accounts hosted on Microsoft Teams |
| numberAssignments | [microsoft.graph.teamsAdministration.numberAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-numberassignment?view=graph-rest-1.0) collection | Represents collection of synchronous telephone number management operations. |
| operations | [microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumberlongrunningoperation?view=graph-rest-1.0) collection | Represents asynchronous telephone number management operation. |
| telephoneNumberManagement | [microsoft.graph.teamsAdministration.telephoneNumberManagementRoot](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumbermanagementroot?view=graph-rest-1.0) | Represents a collection of available telephone number management operations. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.teamsAdminRoot"
}
```
