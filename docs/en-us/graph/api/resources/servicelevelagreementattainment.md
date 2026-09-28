<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/servicelevelagreementattainment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# serviceLevelAgreementAttainment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the Microsoft Entra SLA attainment for a tenant for the identified calendar month.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDate | DateTime | The end date for the calendar month for which SLA attainment is measured. |
| score | Double | The level of SLA attainment achieved by the tenant for the calendar month identified, as described in [Microsoft Entra SLA performance](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/reference-azure-ad-sla-performance). Values are truncated, not rounded, so the actual value is always equal to or higher than the displayed value. Values are expressed as a percentage of availability for the tenant. |
| startDate | DateTime | The start date for the calendar month for which SLA attainment is measured. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceLevelAgreementAttainment",
  "startDate": "DateTime",
  "endDate": "DateTime",
  "score": "Double"
}
```
