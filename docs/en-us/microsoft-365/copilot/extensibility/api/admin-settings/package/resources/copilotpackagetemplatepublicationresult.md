<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagetemplatepublicationresult -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackageTemplatePublicationResult resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents mapping-publication details in the `templatePublication` property of [copilotPackagePublishStepResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishstepresult).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `message` | String | Nullable. Additional template-publication context. |
| `policyProvisioningResults` | [copilotPackagePolicyProvisioningResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyprovisioningresult) collection | Non-nullable. Per-policy results returned by template publication. Can be empty. |
| `resourceId` | String | Nullable. Identifier supplied by template-mapping publication, when available; not proof of a newly created instance, installed package, or effective activated version. |
| `status` | [copilotPackagePolicyProvisioningStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyprovisioningresult#copilotpackagepolicyprovisioningstatus-enumeration) | Nullable. Mapping-publication outcome, separate from HTTP status and Publish step execution. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageTemplatePublicationResult",
  "message": "String",
  "policyProvisioningResults": [
    {
      "@odata.type": "microsoft.graph.copilotPackagePolicyProvisioningResult"
    }
  ],
  "resourceId": "String",
  "status": "String"
}
```
