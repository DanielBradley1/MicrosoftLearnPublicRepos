<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiumfeatureutilization?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# azureADPremiumFeatureUtilization resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the utilization count for a single Microsoft Entra ID premium feature. Contains the number of users who have used the feature. Used by properties of the [azureADPremiumP1FeatureUtilizations](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiump1featureutilizations?view=graph-rest-beta) and [azureADPremiumP2FeatureUtilizations](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiump2featureutilizations?view=graph-rest-beta) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userCount | Int64 | The number of users who have used this premium feature. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureADPremiumFeatureUtilization",
  "userCount": "Integer"
}
```
