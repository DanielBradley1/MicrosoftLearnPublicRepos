<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyselection -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicySelection resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

One selected policy family in [copilotPackagePolicyConfiguration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyconfiguration). The family identifier and its choices must belong to the bound template's applicable catalog.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `policyDefinitionId` | String | Required and non-nullable. Opaque policy-family identifier from the definition catalog, not an individual choice ID. |
| `selections` | [copilotPackagePolicyChoiceSelection](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicychoiceselection) collection | Required and non-nullable. Selected applicable choices, including every required choice in this included family. Missing/null collections, duplicate or unsupported choices are invalid. |

Required choices are checked only within a selected family. The family itself must be selected only when its definition's `requirement` is `mandatory`; default and optional families may be omitted.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicySelection",
  "policyDefinitionId": "String",
  "selections": [
    {
      "@odata.type": "microsoft.graph.copilotPackagePolicyChoiceSelection"
    }
  ]
}
```
