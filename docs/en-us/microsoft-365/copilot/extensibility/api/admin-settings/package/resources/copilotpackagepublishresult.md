<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishresult -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePublishResult resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

The proposed typed value returned by [Publish](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepublishresult-publish), not an updated package. Inspect recorded step and per-policy results even when the HTTP request succeeds.

No aggregate `statusCode` or provider-category property is exposed. Step execution outcome and backend-neutral `operationStatus` remain distinct. A later failure doesn't roll back earlier effects; warnings, partial completion, and unknown effects must not be treated as universal success.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `errorMessage` | String | Nullable. Curated aggregate context; not a stable error identifier or provider-specific contract. |
| `stepResults` | [copilotPackagePublishStepResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishstepresult) collection | Non-nullable. Recorded attempted steps in execution order. An unreached or unrecorded stage isn't evidence of success. |

Optional regular-package acquisition contributes `deploy` after `allow` and before template mapping. Omitted/null installation has no `deploy` entry. Positive existing deployment yields `skipped` without applying the supplied acquisition audience; successful acquisition isn't host-installation or effective-access proof.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePublishResult",
  "errorMessage": "String",
  "stepResults": [
    {
      "@odata.type": "microsoft.graph.copilotPackagePublishStepResult"
    }
  ]
}
```
