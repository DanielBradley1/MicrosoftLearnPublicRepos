<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/statusbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-17 -->

# statusBase resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The statusBase API is deprecated and stopped returning data on December 31, 2021. Going forward, use the new [provisioningStatusInfo](https://learn.microsoft.com/en-us/graph/api/resources/provisioningstatusinfo?view=graph-rest-beta) type.

Describes the status of the provisioning summary event.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| status | provisioningResult | The possible values are: `success`, `warning`, `failure`, `skipped`, `unknownFutureValue`. Supports `$filter` \(`eq`, `contains`\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "status": "String"
}
```
