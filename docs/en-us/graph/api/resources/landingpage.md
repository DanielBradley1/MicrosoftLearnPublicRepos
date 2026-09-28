<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# landingPage resource type

Namespace: microsoft.graph

Represents an attack simulation landing page.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-landingpage?view=graph-rest-1.0) | [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) collection | Get a list of the [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/landingpage-get?view=graph-rest-1.0) | [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) | Get a [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) associated with an attack simulation campaign for a tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who created the landing page. |
| createdDateTime | DateTimeOffset | Date and time when the landing page was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | Description of the landing page as defined by the user. |
| displayName | String | The display name of the landing page. |
| id | String | Unique identifier for the **landingPage** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Email identity of the user who last modified the landing page. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the landing page was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| locale | String | Content locale. |
| source | [simulationContentSource](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationcontentsource-values) | The source of the content. The possible values are: `unknown`, `global`, `tenant`, `unknownFutureValue`. |
| status | [simulationContentStatus](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationcontentstatus-values) | The status of the simulation. The possible values are: `unknown`, `draft`, `ready`, `archive`, `delete`, `unknownFutureValue`. |
| supportedLocales | String collection | Supported locales. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| details | [landingPageDetail](https://learn.microsoft.com/en-us/graph/api/resources/landingpagedetail?view=graph-rest-1.0) collection | The detail information for a landing page associated with a simulation during its creation. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.landingPage",
  "createdBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "lastModifiedDateTime": "String (timestamp)",
  "locale": "String",
  "source": "String",
  "status": "String",
  "supportedLocales": ["String"]
}
```
