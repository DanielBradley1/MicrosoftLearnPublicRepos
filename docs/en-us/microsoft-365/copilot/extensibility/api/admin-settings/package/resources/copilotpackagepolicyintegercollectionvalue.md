<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyintegercollectionvalue -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyIntegerCollectionValue resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

An integer collection derived from [copilotPackagePolicyValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalue), for choices whose trusted constraints require integer collections. Allowed-value catalogs use integer scalars instead.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `values` | Int32 collection | Required, non-nullable, and nonempty. Every element must be a signed 32-bit integer satisfying the choice's trusted constraints. Null or incorrectly typed elements aren't supported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyIntegerCollectionValue",
  "values": ["Int32"]
}
```
