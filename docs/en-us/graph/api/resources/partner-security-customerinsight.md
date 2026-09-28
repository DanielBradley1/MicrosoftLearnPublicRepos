<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-customerinsight?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-31 -->

# customerInsight resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents insights into the security score for a partner's customer.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityscore-list-customerinsights?view=graph-rest-beta) | [microsoft.graph.partner.security.customerInsight](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-customerinsight?view=graph-rest-beta) collection | Get a list of the [customerInsight](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-customerinsight?view=graph-rest-beta) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mfa | [microsoft.graph.partner.security.customerMfaInsight](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-customermfainsight?view=graph-rest-beta) | Details of the customer's Entra tenant MFA policy configuration and usage. |
| tenantId | String | The unique identifier for the customer. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.customerInsight",
  "tenantId": "String (identifier)",
  "mfa": {
    "@odata.type": "microsoft.graph.partner.security.customerMfaInsight"
  }
}
```
