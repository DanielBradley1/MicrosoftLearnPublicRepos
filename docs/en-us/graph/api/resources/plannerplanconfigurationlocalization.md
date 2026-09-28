<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationlocalization?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# plannerPlanConfigurationLocalization resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the localized names for a [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) for a specific language.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/plannerplanconfiguration-list-localizations?view=graph-rest-beta) | [plannerPlanConfigurationLocalization](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationlocalization?view=graph-rest-beta) collection | Get a list of the [plannerPlanConfigurationLocalization](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationlocalization?view=graph-rest-beta) objects and their properties. |
| [Update](https://learn.microsoft.com/en-us/graph/api/plannerplanconfiguration-update?view=graph-rest-beta) | [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) | Add, remove, or update a [plannerPlanConfigurationLocalization](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationlocalization?view=graph-rest-beta) via the update of the plannerPlanConfiguration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| buckets | [plannerPlanConfigurationBucketLocalization](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationbucketlocalization?view=graph-rest-beta) collection | Localized names for configured buckets in the plan configuration. |
| id | String | The unique identifier for the plan configuration location. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| languageTag | String | The language code associated with the localized names in this object. |
| planTitle | String | Localized title of the plan. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerPlanConfigurationLocalization",
  "buckets": [{"@odata.type": "microsoft.graph.plannerPlanConfigurationBucketLocalization"}],
  "id": "String (identifier)",
  "languageTag": "String",
  "planTitle": "String"
  
}
```
