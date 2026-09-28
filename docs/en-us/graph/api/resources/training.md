<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-28 -->

# training resource type

Namespace: microsoft.graph

Represents an attack simulation training.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List trainings](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-trainings?view=graph-rest-1.0) | [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) collection | Get a list of the [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) objects and their properties. |
| [Get training](https://learn.microsoft.com/en-us/graph/api/training-get?view=graph-rest-1.0) | [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) | Get an attack simulation [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) for a tenant. |
| [Get trainingLanguageDetail](https://learn.microsoft.com/en-us/graph/api/traininglanguagedetail-get?view=graph-rest-1.0) | [trainingLanguageDetail](https://learn.microsoft.com/en-us/graph/api/resources/traininglanguagedetail?view=graph-rest-1.0) | Get the [language details](https://learn.microsoft.com/en-us/graph/api/resources/traininglanguagedetail?view=graph-rest-1.0) about an attack simulation training for a tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityStatus | trainingAvailabilityStatus | Training availability status. The possible values are: `unknown`, `notAvailable`, `available`, `archive`, `delete`, `unknownFutureValue`. |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who created the training. |
| createdDateTime | DateTimeOffset | Date and time when the training was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | The description for the training. |
| displayName | String | The display name for the training. |
| durationInMinutes | Int32 | Training duration. |
| hasEvaluation | Boolean | Indicates whether the training has any evaluation. |
| id | String | Unique identifier for the **training** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who last modified the training. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the training was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| source | [simulationContentSource](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationcontentsource-values) | Training content source. The possible values are: `unknown`, `global`, `tenant`, `unknownFutureValue`. |
| supportedLocales | String collection | Supported locales for content for the associated training. |
| tags | String collection | Training tags. |
| type | trainingType | The type of training. The possible values are: `unknown`, `phishing`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| languageDetails | [trainingLanguageDetail](https://learn.microsoft.com/en-us/graph/api/resources/traininglanguagedetail?view=graph-rest-1.0) collection | Language specific details on a training. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.training",
  "availabilityStatus": "String",
  "createdBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "durationInMinutes": "Int32",
  "hasEvaluation": "Boolean",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "lastModifiedDateTime": "String (timestamp)",
  "source": "String",
  "supportedLocales": ["String"],
  "tags": ["String"],
  "type": "String"
}
```
