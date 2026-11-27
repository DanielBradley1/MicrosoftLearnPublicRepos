<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyintegervalue -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyIntegerValue resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A signed 32-bit integer scalar derived from [copilotPackagePolicyValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalue).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `value` | Int32 | Required and non-nullable. Explicit zero is a present value, subject to the choice's constraints; omission/null isn't zero. String and Boolean coercion isn't supported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyIntegerValue",
  "value": "Int32"
}
```
