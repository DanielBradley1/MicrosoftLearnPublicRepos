<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# businessScenario resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a scenario that collects relevant data and configuration for a specific problem domain. For more details about business scenarios, see [Business scenarios API overview](https://learn.microsoft.com/en-us/graph/businessscenarios-concept-overview).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

Note

Currently the business scenario API supports only Planner. The API allows app developers to define a [configuration for a Planner plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta&preserve-view=true) to host scenario-specific tasks, and bring in custom data in each [scenario-specific task](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta&preserve-view=true).

Do you have a scenario that requires bringing in custom data as entities to another Microsoft 365 service? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List businessScenarios](https://learn.microsoft.com/en-us/graph/api/solutionsroot-list-businessscenarios?view=graph-rest-beta) | [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) collection | Get a list of all [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) objects in an organization. |
| [Create businessScenario](https://learn.microsoft.com/en-us/graph/api/solutionsroot-post-businessscenarios?view=graph-rest-beta) | [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) | Create a new [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) object. |
| [Get businessScenario](https://learn.microsoft.com/en-us/graph/api/businessscenario-get?view=graph-rest-beta) | [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) | Read the properties and relationships of a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) object. |
| [Update businessScenario](https://learn.microsoft.com/en-us/graph/api/businessscenario-update?view=graph-rest-beta) | [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) | Update the properties of a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) object. |
| [Delete businessScenario](https://learn.microsoft.com/en-us/graph/api/businessscenario-delete?view=graph-rest-beta) | None | Delete a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) object. The deletion of a scenario causes all data associated with the scenario to be deleted. |
| [Get businessScenarioPlanner](https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-get?view=graph-rest-beta) | [businessScenarioPlanner](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanner?view=graph-rest-beta) | Read the properties and relationships of a [businessScenarioPlanner](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanner?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the user who created the scenario. |
| createdDateTime | DateTimeOffset | The date and time when the scenario was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | Display name of the scenario. |
| id | String | The unique identifier for the scenario. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the user who last modified the scenario. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the scenario was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| ownerAppIds | String collection | Identifiers of applications that are authorized to work with this scenario. |
| uniqueName | String | Unique name of the scenario. To avoid conflicts, the recommended value for the unique name is a reverse domain name format, owned by the author of the scenario. For example, a scenario authored by *Contoso.com* would have a unique name that starts with `com.contoso`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| planner | [businessScenarioPlanner](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanner?view=graph-rest-beta) | Planner content related to the scenario. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.businessScenario",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "ownerAppIds": ["String"],
  "uniqueName": "String"
}
```
