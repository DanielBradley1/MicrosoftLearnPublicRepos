<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# plannerPlanConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration of [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) resources created for a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/plannerplanconfiguration-get?view=graph-rest-beta) | [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) | Read the properties and relationships of a [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/plannerplanconfiguration-update?view=graph-rest-beta) | [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) | Update the properties of a [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) object for a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| buckets | [plannerPlanConfigurationBucketDefinition](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationbucketdefinition?view=graph-rest-beta) collection | List the buckets that should be created in the plan. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the creator of the plan configuration. |
| createdDateTime | DateTimeOffset | The date and time when the plan configuration was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| defaultLanguage | String | The language code for the default language to be used for the names of the objects created for the plan. |
| id | String | The unique identifier for the plan configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the user who last modified the plan configuration. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the plan configuration was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| localizations | [plannerPlanConfigurationLocalization](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationlocalization?view=graph-rest-beta) collection | Localized names for the plan configuration. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerPlanConfiguration",
  "buckets": [{"@odata.type": "microsoft.graph.plannerPlanConfigurationBucketDefinition"}],
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "defaultLanguage": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)"
}
```
