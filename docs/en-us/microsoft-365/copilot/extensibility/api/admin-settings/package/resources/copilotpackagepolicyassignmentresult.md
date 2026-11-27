<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyassignmentresult -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyAssignmentResult resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents assignment details in the `policyAssignment` property of [copilotPackagePublishStepResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishstepresult).

Aggregate `success` doesn't mean every policy was applied. Inspect individual `policyProvisioningResults`, including `skipped` results, and distinguish known applied changes from uncertain partial completion.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `message` | String | Nullable. Additional assignment context. |
| `policyProvisioningResults` | [copilotPackagePolicyProvisioningResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyprovisioningresult) collection | Non-nullable. Per-policy results. |
| `status` | [copilotPackagePolicyProvisioningStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyprovisioningresult#copilotpackagepolicyprovisioningstatus-enumeration) | Nullable. Aggregate policy-assignment outcome; missing is distinct from the enum's unknown sentinel. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyAssignmentResult",
  "message": "String",
  "policyProvisioningResults": [
    {
      "@odata.type": "microsoft.graph.copilotPackagePolicyProvisioningResult"
    }
  ],
  "status": "String"
}
```
