<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicydetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# conditionalAccessPolicyDetail resource type

Namespace: microsoft.graph

Represents the configuration of the **details** property of a Microsoft recommended best-practice [template](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) for a Microsoft Entra [conditional access policy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [conditionalAccessConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessconditionset?view=graph-rest-1.0) | Represents the type of conditions that govern when the policy applies. |
| grantControls | [conditionalAccessGrantControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessgrantcontrols?view=graph-rest-1.0) | Represents grant controls that must be fulfilled for the policy. |
| sessionControls | [conditionalAccessSessionControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrols?view=graph-rest-1.0) | Represents a complex type of session controls that is enforced after sign-in. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessPolicyDetail",
  "conditions": {
    "@odata.type": "microsoft.graph.conditionalAccessConditionSet"
  },
  "grantControls": {
    "@odata.type": "microsoft.graph.conditionalAccessGrantControls"
  },
  "sessionControls": {
    "@odata.type": "microsoft.graph.conditionalAccessSessionControls"
  }
}
```
