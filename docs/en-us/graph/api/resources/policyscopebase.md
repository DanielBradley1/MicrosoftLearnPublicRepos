<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policyscopebase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# policyScopeBase resource type

Namespace: microsoft.graph

Abstract base type defining the scope of applicability for a data governance policy, including locations, activities, and execution mode.

Used as a base type for more specific policy scopes like [policyTenantScope](https://learn.microsoft.com/en-us/graph/api/resources/policytenantscope?view=graph-rest-1.0) and [policyUserScope](https://learn.microsoft.com/en-us/graph/api/resources/policyuserscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activities | microsoft.graph.security.userActivityTypes | Specifies the user activities the calling application supports or is interested in. This flagged enumeration allows multiple members to be selected simultaneously. The possible values are: `none`, `uploadText`, `uploadFile`, `downloadText`, `downloadFile`, `unknownFutureValue`, `copyToClipboard`, `pasteFromClipboard`, `print`, `accessDebugTools`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this evolvable enum: `copyToClipboard`, `pasteFromClipboard`, `print`, `accessDebugTools`. Required. |
| executionMode | microsoft.graph.security.executionMode | Specifies how the policy should be executed. Possible values are `evaluateInline`, `evaluateOffline`, `unknownFutureValue`. Required. |
| locations | Collection\([microsoft.graph.policyLocation](https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-1.0)\) | The locations \(like domains or URLs\) to be protected. Required. |
| policyActions | Collection\([microsoft.graph.dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-1.0)\) | The enforcement actions to take if the policy conditions are met within this scope. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyScopeBase",
  "activities": "String",
  "executionMode": "String",
  "locations": [
    {
      "@odata.type": "microsoft.graph.policyLocation"
    }
  ],
  "policyActions": [
    {
      "@odata.type": "microsoft.graph.dlpActionInfo"
    }
  ]
}
```
