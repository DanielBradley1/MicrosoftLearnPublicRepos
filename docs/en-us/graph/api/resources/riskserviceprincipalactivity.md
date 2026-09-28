<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskserviceprincipalactivity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-28 -->

# riskServicePrincipalActivity resource type

Namespace: microsoft.graph

Represents the risk activity of a Microsoft Entra service principal as determined by Microsoft Entra ID Protection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| detail | [riskDetail](https://learn.microsoft.com/en-us/graph/api/resources/riskdetail?view=graph-rest-1.0) | Details of the detected risk.  <br>**Note:** Details for this property are only available for Workload Identities Premium customers. Events in tenants without this license will be returned `hidden`. |
| riskEventTypes | String collection | The type of risk event detected. The possible values are: `investigationsThreatIntelligence`, `generic`, `adminConfirmedServicePrincipalCompromised`, `suspiciousSignins`, `leakedCredentials`, `anomalousServicePrincipalActivity`, `maliciousApplication`, `suspiciousApplication`. |

## JSON representation

```json
{
    "riskEventTypes": ["String"],
    "detail": "String"
}
```
