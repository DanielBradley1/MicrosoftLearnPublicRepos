<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalue -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyValue resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Abstract base type used by [selected choices](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicychoiceselection) and [allowed scalar values](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalueconstraint). Supply one supported derived type using `@odata.type`; the base type can't be instantiated.

| Derived type | Required member | Meaning |
| :--- | :--- | :--- |
| [copilotPackagePolicyBooleanValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicybooleanvalue) | `value` | Boolean scalar. Explicit false isn't omission. |
| [copilotPackagePolicyIntegerValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyintegervalue) | `value` | Signed 32-bit integer scalar. Explicit zero isn't omission. |
| [copilotPackagePolicyStringValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicystringvalue) | `value` | Nonempty string scalar. |
| [copilotPackagePolicyIntegerCollectionValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyintegercollectionvalue) | `values` | Nonempty integer collection. |
| [copilotPackagePolicyStringCollectionValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicystringcollectionvalue) | `values` | Nonempty string collection. |

The chosen type and each value must satisfy the choice's trusted constraints. Arbitrary JSON, unknown or abstract type discriminators, Boolean collections, type coercion, missing required members, and null collection elements aren't supported. Allowed-value catalogs contain scalar variants only.

## Methods

None.

## Properties

None. Supported derived types define their required value member.

## Relationships

None.

## JSON representation

The following JSON representation shows the abstract resource type, which declares no properties. It isn't an instantiable request value; use a supported derived type for configured values.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyValue"
}
```
