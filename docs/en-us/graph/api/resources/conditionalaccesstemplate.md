<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-03 -->

# conditionalAccessTemplate resource type

Namespace: microsoft.graph

Represents a Microsoft recommended template of best practice configurations for Microsoft Entra [conditional access policies](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). For more information, see [Conditional Access policy templates](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policy-common).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-list-templates?view=graph-rest-1.0) | [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) collection | Get a list of the [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/conditionalaccesstemplate-get?view=graph-rest-1.0) | [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) | Read the properties and relationships of a [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The user-friendly name of the template. |
| details | [conditionalAccessPolicyDetail](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicydetail?view=graph-rest-1.0) | Complete list of policy details specific to the template. This property contains the JSON of policy settings for configuring a Conditional Access policy. |
| id | String | Immutable ID of a template. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| name | String | The user-friendly name of the template. |
| scenarios | templateScenarios | List of conditional access scenarios that the template is recommended for. The possible values are: `new`, `secureFoundation`, `zeroTrust`, `remoteWork`, `protectAdmins`, `emergingThreats`, `unknownFutureValue`. This is a multi-valued enum. Supports `$filter` \(`has`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessTemplate",
  "description": "String",
  "details": {
    "@odata.type": "microsoft.graph.conditionalAccessPolicyDetail",
  "id": "String (identifier)",
  "name": "String",
  "scenarios": "String"
  }
}
```
