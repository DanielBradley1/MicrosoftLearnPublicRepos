<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemailauthenticationdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# analyzedEmailAuthenticationDetail resource type

Namespace: microsoft.graph.security

Represents a list of pass or fail verdicts by email authentication protocols such as DMARC, DKIM, SPF, or a combination of multiple authentication types \(CompAuth\). It's returned in the **authenticationDetails** property of [analyzedEmail](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| compositeAuthentication | String | A value used by Microsoft 365 to combine email authentication such as SPF, DKIM, and DMARC, to determine whether the message is authentic. |
| dkim | String | DomainKeys identified mail \(DKIM\). Indicates whether it was pass/fail/soft fail. |
| dmarc | String | Domain-based Message Authentication. Indicates whether it was pass/fail/soft fail. |
| senderPolicyFramework | String | Sender Policy Framework \(SPF\). Indicates whether it was pass/fail/soft fail. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.analyzedEmailAuthenticationDetail",
  "dmarc": "String",
  "dkim": "String",
  "senderPolicyFramework": "String",
  "compositeAuthentication": "String"
}
```
