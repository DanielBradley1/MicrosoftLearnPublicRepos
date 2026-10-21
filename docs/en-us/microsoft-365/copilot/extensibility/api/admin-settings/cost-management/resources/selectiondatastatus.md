<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/selectiondatastatus -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# selectionDataStatus resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Freshness of each source that contributed to a computed balance or selection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `evaluatedDateTime` | DateTimeOffset | When the result was evaluated. |
| `groupMembershipAsOfDateTime` | DateTimeOffset | Nullable. As-of time of the group membership used. |
| `policyConfigurationAsOfDateTime` | DateTimeOffset | Nullable. As-of time of the policy configuration used. |
| `usageAsOfDateTime` | DateTimeOffset | As-of time of the usage data used. Omitted when no usage read was performed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.selectionDataStatus",
  "evaluatedDateTime": "DateTimeOffset",
  "groupMembershipAsOfDateTime": "DateTimeOffset",
  "policyConfigurationAsOfDateTime": "DateTimeOffset",
  "usageAsOfDateTime": "DateTimeOffset"
}
```
