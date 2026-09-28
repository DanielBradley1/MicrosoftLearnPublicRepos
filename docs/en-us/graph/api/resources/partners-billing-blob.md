<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-blob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# blob resource type

Namespace: microsoft.graph.partners.billing

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Represents a billing blob that contains exported data.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The blob name. |
| partitionValue | String | The partition that contains the file. A large partition is split into multiple files, each with the same **partitionValue**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "String",
  "partitionValue": "String"
}
```
