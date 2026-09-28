<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolbillingconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcAgentPoolBillingConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the billing configuration for a Cloud PC agent pool.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| billingPlanId | String | The identifier of the billing plan. |
| billingType | [cloudPcAgentPoolBillingType](#cloudpcagentpoolbillingtype-values) | The type of billing for the agent pool. The possible values are: `payAsYouGo`, `unknownFutureValue`. The default value is `payAsYouGo`. |

### cloudPcAgentPoolBillingType values

| Member | Description |
| :--- | :--- |
| payAsYouGo | Indicates that the billing type is associated with a pay‑as‑you‑go model. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAgentPoolBillingConfiguration",
  "billingPlanId": "String",
  "billingType": "String"
}
```
