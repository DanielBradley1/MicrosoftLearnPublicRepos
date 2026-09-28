<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionsanalyticsaggregatedidentitysummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsAnalyticsAggregatedIdentitySummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the total number of identities of a specific kind, for example, roles, and the number of a specific finding for that identity, for example, inactive roles, in an authorization system.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| findingsCount | Int32 | The total number of identities of a specific kind that has a specific finding type. |
| totalCount | Int32 | The total number of identities in an authorization system that Permissions Management checked for a specific finding. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsAnalyticsAggregatedIdentitySummary",
  "totalCount": "Integer",
  "findingsCount": "Integer"
}
```
