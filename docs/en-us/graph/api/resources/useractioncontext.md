<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/useractioncontext?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# userActionContext resource type

Namespace: microsoft.graph

Represents the user action that the authenticating identity is performing, as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0). Inherits from [signInContext](https://learn.microsoft.com/en-us/graph/api/resources/signincontext?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userAction | userAction | Represents the user action that the authenticating identity is performing. The possible values are: `registerSecurityInformation`, `registerOrJoinDevices`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userActionContext",
  "userAction": "String"
}
```
