<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-accountobjectidaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# accountObjectIdAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta) that targets an account by Microsoft Entra object ID from a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) hunting query. The action uses the configured account object ID column from the query output to identify the account.

Inherits from [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountObjectIdColumn | String | Name of the hunting-query result column that contains the Microsoft Entra object ID of the targeted account. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.accountObjectIdAction",
  "accountObjectIdColumn": "String"
}
```
