<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/includeallaccounttargetcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# includeAllAccountTargetContent resource type

Namespace: microsoft.graph

Represents all users of a tenant who should be selected for a targeted phishing simulation.

Inherits from [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [accountTargetContentType](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0#accounttargetcontenttype-values) | The type of account target content. The possible values are: `unknown`, `includeAll`, `addressBook`, `unknownFutureValue`. Inherited from [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.security.includeAllAccountTargetContent",
    "type": "String"
}
```

## Related content

- [Simulate a phishing attack](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training?view=o365-worldwide&preserve-view=true)
- [Get started using attack simulation training](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training-get-started?view=o365-worldwide&preserve-view=true#simulations).
