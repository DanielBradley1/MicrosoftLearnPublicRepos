<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicychoiceselection -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyChoiceSelection resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

One applicable choice selected within [copilotPackagePolicySelection](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyselection). It isn't a policy-definition object or independently addressable resource.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `choiceId` | String | Required and non-nullable. Opaque choice identifier within the selected policy family. |
| `value` | [copilotPackagePolicyValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalue) | Nullable. Configurable choices require a non-null supported derived value satisfying the catalog's trusted type, cardinality, and allowed-value constraints. Reference-only choices require omission or null. |

A verified unconfigured saved value may be returned as null; malformed or unavailable saved data returns an error instead. Nullable read values don't authorize null writes for configurable choices. Explicit Boolean false and integer zero remain present values.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyChoiceSelection",
  "choiceId": "String",
  "value": {
    "@odata.type": "microsoft.graph.copilotPackagePolicyValue"
  }
}
```
