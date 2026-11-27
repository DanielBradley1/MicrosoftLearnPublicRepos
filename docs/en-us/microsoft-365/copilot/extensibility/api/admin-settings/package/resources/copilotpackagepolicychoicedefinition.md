<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicychoicedefinition -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyChoiceDefinition resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

One supported choice within [copilotPackagePolicyDefinition](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicydefinition). It describes an applicable choice, not a saved selection or independently addressable resource.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `displayName` | String | Non-nullable. Display name of the supported choice. |
| `id` | String | Non-nullable. Opaque choice identifier within its policy family; use it as `choiceId`. |
| `isRequired` | Boolean | Non-nullable. Whether this choice must be selected when the family is included. Doesn't make an optional/default family mandatory. Unknown requiredness is an error, not false. |
| `valueConstraint` | [copilotPackagePolicyValueConstraint](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalueconstraint) | Nullable. Null identifies a verified reference-only choice, which requires an omitted/null selected value. Missing or malformed constraint evidence returns an error, not null. |

Configurable choices require a supported non-null typed selected value satisfying the trusted constraints. Saved unconfigured values can be null; that doesn't make null a valid configured write.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyChoiceDefinition",
  "displayName": "String",
  "id": "String",
  "isRequired": "Boolean",
  "valueConstraint": {
    "@odata.type": "microsoft.graph.copilotPackagePolicyValueConstraint"
  }
}
```
