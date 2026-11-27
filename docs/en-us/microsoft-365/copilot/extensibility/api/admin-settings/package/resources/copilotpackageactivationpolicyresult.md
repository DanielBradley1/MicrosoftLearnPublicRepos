<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageactivationpolicyresult -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackageActivationPolicyResult resource type

This reference describes only the beta contract. Select **beta** to view it; availability depends on the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A per-policy value in [copilotPackageActivationStep](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageactivationstep). This native activation status vocabulary is separate from the Publish provisioning-status vocabulary.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `displayName` | String | Nullable. Human-readable policy label, not an identifier. |
| `message` | String | Nullable. Curated developer-readable outcome text; not a stable branch key or raw partner exception. |
| `policyId` | String | Nullable. Identifier of the reported policy, not the selected template ID. |
| `status` | copilotPackagePolicyResultStatus | Non-nullable. Individual policy outcome. A tolerated `failed` value can coexist with an overall warning success. |
| `workload` | [copilotPackagePolicyWorkloadType](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyprovisioningresult#copilotpackagepolicyworkloadtype-enumeration) | Nullable. Policy domain. `purview`, `defender`, `entra`, or `sharePoint`; null means missing, while unrecognized values normalize to `unknownFutureValue`. |

### copilotPackagePolicyResultStatus enumeration

| Value | Description |
| :--- | :--- |
| `succeeded` | Policy operation reported success. |
| `failed` | Policy operation failed. |
| `skipped` | Policy operation wasn't executed. |
| `conflict` | Policy operation reported a conflict. |
| `warning` | Policy operation reported a warning. |
| `unknownFutureValue` | Reserved for enum evolution. |

The reviewed workload mapping doesn't establish support for the standard `Prefer: include-unknown-enum-members` header. Don't conflate missing values with a normalized unknown member.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageActivationPolicyResult",
  "displayName": "String",
  "message": "String",
  "policyId": "String",
  "status": "String",
  "workload": "String"
}
```
