<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiump2featureutilizations?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# azureADPremiumP2FeatureUtilizations resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the utilization data for Microsoft Entra ID P2 premium features. Each property contains a user count indicating how many users in the tenant have used that P2 feature. Used by the **p2FeatureUtilizations** property of the [azureADPremiumLicenseInsight](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiumlicenseinsight?view=graph-rest-beta) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| riskBasedConditionalAccess | [azureADPremiumFeatureUtilization](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiumfeatureutilization?view=graph-rest-beta) | The utilization data for the risk-based Conditional Access feature. |
| riskBasedConditionalAccessGuestUsers | [azureADPremiumFeatureUtilization](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiumfeatureutilization?view=graph-rest-beta) | The utilization data for the risk-based Conditional Access feature applied to guest users. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureADPremiumP2FeatureUtilizations",
  "riskBasedConditionalAccess": {
    "@odata.type": "microsoft.graph.azureADPremiumFeatureUtilization"
  },
  "riskBasedConditionalAccessGuestUsers": {
    "@odata.type": "microsoft.graph.azureADPremiumFeatureUtilization"
  }
}
```
