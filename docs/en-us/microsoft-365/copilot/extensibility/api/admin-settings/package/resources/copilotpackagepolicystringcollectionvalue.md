<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicystringcollectionvalue -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyStringCollectionValue resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A string collection derived from [copilotPackagePolicyValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalue), for choices whose trusted constraints require string collections. Allowed-value catalogs use string scalars instead.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `values` | String collection | Required, non-nullable, and nonempty. Strings are preserved without trimming or type coercion; each must satisfy the choice's trusted constraints. Null or incorrectly typed elements aren't supported. |

This contract doesn't impose a universal collection-size limit or nonempty-element rule beyond the trusted constraints.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyStringCollectionValue",
  "values": ["String"]
}
```
