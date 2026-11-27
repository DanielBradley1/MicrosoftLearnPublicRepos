<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishscope -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePublishScope resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents the publication audience supplied in the `publishScope` parameter of [Publish](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepublishresult-publish).

This complex type describes availability, not installation or permission consent.

Use the separate [copilotPackageInstallScope](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageinstallscope) parameter for optional regular-package acquisition during Publish. Publication `noOne` isn't an installation choice, and this type's `policyType` isn't accepted in `installScope`.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `policyType` | copilotPackageAssignmentPolicyType | Optional and nullable. Availability-policy category; omission/null defaults to `allowAccess`. This isn't a per-policy workload. Legacy fallback behavior doesn't establish the proposed strict typed contract. |
| `principals` | [copilotPackagePublishPrincipal](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishprincipal) collection | Required and non-nullable. Explicit audience members. Nonempty for `specificUsers`; supply `[]` when no explicit members are selected. |
| `scope` | copilotPackageAudienceScope | Required and non-nullable. The availability audience. |

### copilotPackageAudienceScope enumeration

| Value | Description |
| :--- | :--- |
| `specificUsers` | Explicit selected principals. |
| `everyone` | Availability for everyone. |
| `noOne` | No availability audience selected. Not an accepted installation audience. |
| `unknownFutureValue` | Reserved for enum evolution; not an accepted input. |

### copilotPackageAssignmentPolicyType enumeration

| Value | Description |
| :--- | :--- |
| `allowAccess` | Availability/access policy category; default for omission/null. |
| `allowOnboarding` | Onboarding-availability policy category. |
| `unknownFutureValue` | Reserved for enum evolution; not an accepted typed input. |

This is the proposed beta typed contract. Matching backend admission is a cutover requirement; acceptance or fallback of legacy provider strings isn't a documented strict-input capability.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePublishScope",
  "policyType": "String",
  "principals": [
    {
      "@odata.type": "microsoft.graph.copilotPackagePublishPrincipal"
    }
  ],
  "scope": "String"
}
```
