<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicytemplate -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyTemplate resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a tenant policy template used for Copilot package publication or native template activation.

The `policyTemplates` collection under `/copilot/admin/catalog` returns summaries. A keyed read returns saved selected configuration; the separate template-bound definition catalog returns complete applicable choices, not saved selections or internal policy metadata.

Use an applicable template's `id` as the required `policyTemplateId` of [Publish](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepublishresult-publish) or native [Activate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackageactivationresult-activate). Publish's request-local customization doesn't save the template. Activate later resolves fresh saved settings for that ID rather than a prior Publish snapshot.

This is the proposed beta contract, requiring matching schema and receiving-service release. It doesn't establish live V1 availability, template-write deployment, or application-only backend execution.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-list) | [copilotPackagePolicyTemplate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicytemplate) collection | Get available policy-template metadata. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-get) | [copilotPackagePolicyTemplate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicytemplate) | Read one template and its saved selected configuration. |
| [Update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-update) | None. | Save guarded changes to an existing writable custom template; no upsert or protected/default writes. |
| [List policy definitions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicydefinition-list) | [copilotPackagePolicyDefinition](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicydefinition) collection | Read the complete applicable definitions and choices for this template. |
| [Copy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-copy) | [copilotPackagePolicyTemplate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicytemplate) | Create one new custom template by copying its source on the server. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `description` | String | Nullable. Explanatory text. Update omission preserves it; null clears it. Copy omission inherits the source description; null clears it on the new template. |
| `displayName` | String | Non-nullable. Human-readable name. Copy requires a nonempty value. Updates require a writable custom target; omitted name is preserved. |
| `id` | String | Non-nullable and computed. Opaque server-generated template identifier; configured defaults have their own IDs. Use the returned value; it isn't writable. |
| `policyConfiguration` | [copilotPackagePolicyConfiguration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyconfiguration) | Nullable. Saved selected settings on keyed detail. Null means verified unconfigured; malformed/unavailable saved data returns an error. Summary responses omit this member. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `policyDefinitions` | [copilotPackagePolicyDefinition](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicydefinition) collection | Complete applicable supported definitions and choices in one template-bound read. Read-only; no keyed definition GET, paging, or expansion on template summaries. |

## JSON representation

The following JSON representation shows the resource type. Summary responses omit `policyConfiguration`; keyed detail can return null for a verified unconfigured template.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyTemplate",
  "description": "String",
  "displayName": "String",
  "id": "String",
  "policyConfiguration": {
    "@odata.type": "microsoft.graph.copilotPackagePolicyConfiguration"
  }
}
```
