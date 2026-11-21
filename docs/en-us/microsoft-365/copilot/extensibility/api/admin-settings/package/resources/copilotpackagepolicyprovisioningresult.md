<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyprovisioningresult -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyProvisioningResult resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents one member of the `policyProvisioningResults` collection in [copilotPackagePolicyAssignmentResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyassignmentresult) or [copilotPackageTemplatePublicationResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagetemplatepublicationresult).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `message` | String | Nullable. Additional policy outcome context. |
| `policyCategory` | String | Nullable. Free-form policy category supplied by the service. |
| `policyId` | String | Nullable. Service-provided policy identifier. |
| `policyName` | String | Nullable. Human-readable policy name. |
| `policyType` | copilotPackagePolicyWorkloadType | Nullable. Policy domain, separate from [availability policyType](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishscope). Missing remains null; unrecognized native values normalize to `unknownFutureValue`. |
| `status` | copilotPackagePolicyProvisioningStatus | Non-nullable. Individual provisioning outcome, distinct from step execution `succeeded`. |

### copilotPackagePolicyWorkloadType enumeration

| Value | Description |
| :--- | :--- |
| `purview` | Microsoft Purview policy domain. |
| `defender` | Microsoft Defender policy domain. |
| `entra` | Microsoft Entra policy domain. |
| `sharePoint` | SharePoint policy domain. |
| `unknownFutureValue` | Unrecognized or future policy domain, distinct from missing/null. |

### copilotPackagePolicyProvisioningStatus enumeration

| Value | Description |
| :--- | :--- |
| `success` | Provisioning reported success. Not the step-outcome literal `succeeded`. |
| `failed` | Provisioning failed. |
| `skipped` | Provisioning wasn't executed; not evidence the policy was applied. |
| `resolveConflict` | Provisioning requires conflict resolution. |
| `warning` | Provisioning reported a warning. |
| `unknownFutureValue` | Reserved for enum evolution. |

This proposed typed mapping does not establish standard `Prefer: include-unknown-enum-members` behavior or guarantee every policy was applied.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyProvisioningResult",
  "message": "String",
  "policyCategory": "String",
  "policyId": "String",
  "policyName": "String",
  "policyType": "String",
  "status": "String"
}
```
