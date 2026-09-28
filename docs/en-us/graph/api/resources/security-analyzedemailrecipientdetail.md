<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemailrecipientdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# analyzedEmailRecipientDetail resource type

Namespace: microsoft.graph.security

Details about the recipient or recipients as mentioned in the email. It's returned in the **recipientDetail** property of [analyzedEmail](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ccRecipients | String collection | Recipient address in the cc field. |
| domainName | String | Domain name of the recipient. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.analyzedEmailRecipientDetail",
  "domainName": "String",
  "ccRecipients": [
    "String"
  ]
}
```
