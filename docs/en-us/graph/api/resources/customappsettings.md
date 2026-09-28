<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customappsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-14 -->

# customAppSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents tenant-wide custom app settings for all [Microsoft Teams apps](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| developerToolsForShowingAppUsageMetrics | [appDevelopmentPlatforms](https://learn.microsoft.com/en-us/graph/api/resources/customappsettings?view=graph-rest-beta#appdevelopmentplatforms-values) | A comma-separated list of developer tools that are allowed to display app usage metrics. The possible values are: `developerPortal`, `unknownFutureValue`. |

### appDevelopmentPlatforms values

| Member | Description |
| :--- | :--- |
| developerPortal | Enables the developer portal to display app usage metrics. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customAppSettings",
  "developerToolsForShowingAppUsageMetrics": "String"
}
```
