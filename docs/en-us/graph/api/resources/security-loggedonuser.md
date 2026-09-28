<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-loggedonuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# loggedOnUser resource type

Namespace: microsoft.graph.security

User that was loggen on the machine during the time of the alert.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountName | String | User account name of the logged-on user. |
| domainName | String | User account domain of the logged-on user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.loggedOnUser",
  "accountName": "String",
  "domainName": "String"
}
```
