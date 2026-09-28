<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# loginPage resource type

Namespace: microsoft.graph

Represents an attack simulation login page.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-loginpage?view=graph-rest-1.0) | [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) collection | Get a list of the [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/loginpage-get?view=graph-rest-1.0) | [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) | Get a [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) associated with an attack simulation campaign for a tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The HTML content of the login page. |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who created the login page. |
| createdDateTime | DateTimeOffset | Date and time when the login page was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | Description about the login page. |
| displayName | String | Display name of the login page. |
| id | String | Unique identifier for the **loginPage** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| language | String | The content language of the login page. |
| lastModifiedBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who last modified the login page. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the login page was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| source | [simulationContentStatus](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationcontentsource-values) | The source of the content. The possible values are: `unknown`, `global`, `tenant`, `unknownFutureValue`. |
| status | [simulationContentStatus](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationcontentstatus-values) | The login page status. The possible values are: `unknown`, `draft`, `ready`, `archive`, `delete`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.loginPage",
  "content": "String",
  "createdBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "language": "String",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "lastModifiedDateTime": "String (timestamp)",
  "source": "String",
  "status": "String"
}
```
