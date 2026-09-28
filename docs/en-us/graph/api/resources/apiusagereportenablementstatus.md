<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/apiusagereportenablementstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# apiUsageReportEnablementStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the enablement status of a specific API usage report metric for SharePoint. This resource indicates whether a particular metric is collected and reported.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| metric | String | The name of the API usage report metric. The supported values are: `egressReport`, `throttlingReport`. |
| onboardingStatus | apiUsageReportOnboardingStatus | The current onboarding status of the metric. The possible values are: `enabling`, `enabled`, `disabling`, `disabled`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.apiUsageReportEnablementStatus",
  "metric": "String",
  "onboardingStatus": "String"
}
```
