<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# prompt resource type \(for securityCopilot\)

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a prompt in a Security Copilot [session](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-session?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-session-list-prompts?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.prompt](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta) collection | Get a list of the prompt objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-session-post-prompts?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.prompt](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta) | Create a new prompt object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-prompt-get?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.prompt](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.security.securityCopilot.prompt](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | Input content to the prompt. |
| createdDateTime | DateTimeOffset | Created time. |
| id | String | Represents the unique ID of the Security Copilot prompt. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| inputs | [microsoft.graph.Dictionary](https://learn.microsoft.com/en-us/graph/api/resources/dictionary?view=graph-rest-beta) | Not implemented. |
| lastModifiedDateTime | DateTimeOffset | Last modified time. |
| skillInputDescriptors | [microsoft.graph.security.securityCopilot.skillInputDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-skillinputdescriptor?view=graph-rest-beta) collection | Skill Input descriptor. |
| skillName | String | Skill name. |
| type | microsoft.graph.security.securityCopilot.promptType | Prompt types. The possible values are: `unknown`, `context`, `prompt`, `skill`, `feedback`, `unknownFutureValue`. Only `prompt` is currently supported. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| evaluations | [microsoft.graph.security.securityCopilot.evaluation](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-evaluation?view=graph-rest-beta) collection | Collection of evaluations |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.prompt",
  "id": "String (identifier)",
  "type": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "skillName": "String",
  "skillInputDescriptors": [
    {
      "@odata.type": "microsoft.graph.security.securityCopilot.skillInputDescriptor"
    }
  ],
  "content": "String",
  "inputs": {
    "@odata.type": "microsoft.graph.Dictionary"
  }
}
```
