<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# accountTargetContent resource type

Namespace: microsoft.graph

Represents included or excluded users for an attack simulation training campaign.

Base type of [addressBookAccountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/addressbookaccounttargetcontent?view=graph-rest-1.0) and [includeAllAccountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/includeallaccounttargetcontent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [accountTargetContentType](#accounttargetcontenttype-values) | The type of account target content. The possible values are: `unknown`, `includeAll`, `addressBook`, `unknownFutureValue`. |

### accountTargetContentType values

| Member | Description |
| :--- | :--- |
| unknown | Unknown type. |
| includeAll | Include all users under tenant boundary. |
| addressBook | Account details uploaded via Azure Active Directory. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accountTargetContent",
  "type": "String"
}
```

## Related content

- [Simulate a phishing attack](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training?view=o365-worldwide&preserve-view=true)
- [Get started using attack simulation training](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training-get-started?view=o365-worldwide&preserve-view=true#simulations).
