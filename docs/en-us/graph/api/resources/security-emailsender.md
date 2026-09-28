<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-emailsender?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# emailSender resource type

Namespace: microsoft.graph.security

Email sender common properties.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the sender. |
| domainName | String | Sender domain. |
| emailAddress | String | Sender email address. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.emailSender",
  "emailAddress": "String",
  "displayName": "String",
  "domainName": "String"
}
```
