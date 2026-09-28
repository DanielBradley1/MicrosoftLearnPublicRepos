<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/informationalurl?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# informationalUrl resource type

Namespace: microsoft.graph

Basic profile information of the application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| logoUrl | String | CDN URL to the application's logo, Read-only. |
| marketingUrl | String | Link to the application's marketing page. For example, `https://www.contoso.com/app/marketing` |
| privacyStatementUrl | String | Link to the application's privacy statement. For example, `https://www.contoso.com/app/privacy` |
| supportUrl | String | Link to the application's support page. For example, `https://www.contoso.com/app/support` |
| termsOfServiceUrl | String | Link to the application's terms of service statement. For example, `https://www.contoso.com/app/termsofservice` |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "logoUrl": "String",
  "marketingUrl": "String",
  "privacyStatementUrl": "String",
  "supportUrl": "String",
  "termsOfServiceUrl": "String"
}
```
