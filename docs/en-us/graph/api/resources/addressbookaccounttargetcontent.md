<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/addressbookaccounttargetcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# addressBookAccountTargetContent resource type

Namespace: microsoft.graph

Represents included or excluded users' email addresses for an attack simulation training campaign.

Inherits from [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountTargetEmails | String collection | List of user emails targeted for an attack simulation training campaign. |
| type | [accountTargetContentType](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0#accounttargetcontenttype-values) | The type of account target content contains targeted user email addresses. The possible values are: `unknown`, `includeAll`, `addressBook`, `unknownFutureValue`. Inherited from [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.security.addressBookAccountTargetContent",
    "accountTargetEmails": ["String"],
    "type": "String"
}
```

## Related content

- [Simulate a phishing attack](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training?view=o365-worldwide&preserve-view=true)
- [Get started using attack simulation training](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training-get-started?view=o365-worldwide&preserve-view=true#simulations).
