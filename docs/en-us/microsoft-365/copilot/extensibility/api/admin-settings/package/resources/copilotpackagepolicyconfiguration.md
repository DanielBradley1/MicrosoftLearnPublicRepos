<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyconfiguration -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyConfiguration resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A complete selected policy set, not an overlay on saved settings. Used in saved [template detail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-get), explicit [Update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-update) or [Copy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-copy), and request-local [Publish](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepublishresult-publish) customization.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `policies` | [copilotPackagePolicySelection](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyselection) collection | Required and non-nullable. Complete selected family set. Missing/null collections and duplicate, unknown, stale, or unauthorized identifiers are invalid. |

Consult the bound template's complete [policy definitions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicydefinition-list). Include every applicable `mandatory` family. `default` and `optional` families may be omitted; omitted families aren't inserted into a supplied replacement set. Every included family must select all of its required choices.

An explicit empty `policies` collection is valid when no applicable mandatory family exists, even when default or optional families have required choices. This differs from an omitted/null configuration, whose meaning depends on the operation:

| Operation | Configuration omitted | Configuration null | Configuration object |
| :--- | :--- | :--- | :--- |
| Publish | Use saved template settings. | Use saved template settings. | Use the complete set only for this request; don't save it. |
| Update template | Preserve saved settings. | Invalid; HTTP 400. | Save the complete replacement set. |
| Copy template | Copy raw source settings. | Copy raw source settings. | Validate and use the complete replacement set on the new template. |

Native Activate subsequently resolves fresh saved settings for its required `policyTemplateId`; it doesn't automatically reuse a prior Publish configuration.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyConfiguration",
  "policies": [
    {
      "@odata.type": "microsoft.graph.copilotPackagePolicySelection"
    }
  ]
}
```
