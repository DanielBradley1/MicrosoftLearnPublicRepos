<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-accountsidaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# accountSidAction resource type

Namespace: microsoft.graph.security

Represents an [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-1.0) that targets an account by security identifier \(SID\) from a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) hunting query. The action uses the configured account SID column from the query output to identify the account.

Inherits from [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountSidColumn | String | Name of the hunting-query result column that contains the SID of the targeted account. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.accountSidAction",
  "accountSidColumn": "String"
}
```
