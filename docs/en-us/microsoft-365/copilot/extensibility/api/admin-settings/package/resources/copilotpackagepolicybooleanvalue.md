<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicybooleanvalue -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyBooleanValue resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A Boolean scalar derived from [copilotPackagePolicyValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalue), used in selected choices or allowed scalar values.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `value` | Boolean | Required and non-nullable. Explicit false is a valid present value, subject to the choice's allowed values; omission/null isn't false. String or numeric coercion and Boolean collections aren't supported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyBooleanValue",
  "value": "Boolean"
}
```
