<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepermissionconsentresult -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePermissionConsentResult resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents the consent-status details in the `permissionConsent` property of [copilotPackagePublishStepResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishstepresult).

This result describes a validation check, not a permission-consent grant.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `missingPermissions` | String collection | Non-nullable. Missing permission names. An empty collection doesn't establish every other prerequisite for publication. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePermissionConsentResult",
  "missingPermissions": ["String"]
}
```
