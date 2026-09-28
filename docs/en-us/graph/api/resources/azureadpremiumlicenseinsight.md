<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiumlicenseinsight?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# azureADPremiumLicenseInsight resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides insight into the Microsoft Entra ID P1 and P2 premium license utilization for a tenant. This resource shows how many premium licenses are entitled and how the associated premium features are being used.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/azureadpremiumlicenseinsight-get?view=graph-rest-beta) | [azureADPremiumLicenseInsight](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiumlicenseinsight?view=graph-rest-beta) | Get the premium license utilization insight for the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| entitledP1LicenseCount | Int64 | The number of Microsoft Entra ID P1 licenses entitled to the tenant. |
| entitledP2LicenseCount | Int64 | The number of Microsoft Entra ID P2 licenses entitled to the tenant. |
| entitledTotalLicenseCount | Int64 | The total number of Microsoft Entra ID premium licenses \(P1 + P2\) entitled to the tenant. |
| id | String | The unique identifier for the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| internetAccessFeatureUtilizations | [internetAccessFeatureUtilizations](https://learn.microsoft.com/en-us/graph/api/resources/internetaccessfeatureutilizations?view=graph-rest-beta) | The utilization data for Microsoft Entra Internet Access features. |
| p1FeatureUtilizations | [azureADPremiumP1FeatureUtilizations](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiump1featureutilizations?view=graph-rest-beta) | The utilization data for Microsoft Entra ID P1 features. |
| p2FeatureUtilizations | [azureADPremiumP2FeatureUtilizations](https://learn.microsoft.com/en-us/graph/api/resources/azureadpremiump2featureutilizations?view=graph-rest-beta) | The utilization data for Microsoft Entra ID P2 features. |
| privateAccessFeatureUtilizations | [privateAccessFeatureUtilizations](https://learn.microsoft.com/en-us/graph/api/resources/privateaccessfeatureutilizations?view=graph-rest-beta) | The utilization data for Microsoft Entra Private Access features. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureADPremiumLicenseInsight",
  "entitledP1LicenseCount": "Integer",
  "entitledP2LicenseCount": "Integer",
  "entitledTotalLicenseCount": "Integer",
  "id": "String (identifier)",
  "internetAccessFeatureUtilizations": {
    "@odata.type": "microsoft.graph.internetAccessFeatureUtilizations"
  },
  "p1FeatureUtilizations": {
    "@odata.type": "microsoft.graph.azureADPremiumP1FeatureUtilizations"
  },
  "p2FeatureUtilizations": {
    "@odata.type": "microsoft.graph.azureADPremiumP2FeatureUtilizations"
  },
  "privateAccessFeatureUtilizations": {
    "@odata.type": "microsoft.graph.privateAccessFeatureUtilizations"
  }
}
```
