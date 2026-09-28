<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customclaimbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# customClaimBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract type for a custom claim. It contains a collection of configurations for a claim.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configurations | [customClaimConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customclaimconfiguration?view=graph-rest-beta) collection | One or more configurations that describe how the claim is sourced and under what conditions. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customClaimBase",
  "configurations": [
    {
      "@odata.type": "microsoft.graph.customClaimConfiguration"
    }
  ]
}
```
