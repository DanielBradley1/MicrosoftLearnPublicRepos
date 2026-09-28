<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privateaccessfeatureutilizations?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# privateAccessFeatureUtilizations resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the aggregated utilization metrics for Microsoft Entra Private Access features. Used by the **privateAccessFeatureUtilizations** property of the [azureADPremiumLicenseInsight](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiumlicenseinsight?view=graph-rest-beta) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| privateAccess | [azureADPremiumFeatureUtilization](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiumfeatureutilization?view=graph-rest-beta) | The utilization data for the Microsoft Entra Private Access feature. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privateAccessFeatureUtilizations",
  "privateAccess": {
    "@odata.type": "microsoft.graph.azureADPremiumFeatureUtilization"
  }
}
```
