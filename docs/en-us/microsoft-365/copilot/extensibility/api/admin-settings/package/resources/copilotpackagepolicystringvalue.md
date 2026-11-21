<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicystringvalue -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyStringValue resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A string scalar derived from [copilotPackagePolicyValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalue).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `value` | String | Required, non-nullable, and nonempty. Preserved without trimming or type coercion and subject to the choice's allowed-value constraints. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyStringValue",
  "value": "String"
}
```
