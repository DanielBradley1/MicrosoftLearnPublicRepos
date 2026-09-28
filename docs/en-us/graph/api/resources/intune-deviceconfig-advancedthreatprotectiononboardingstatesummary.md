<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingstatesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# advancedThreatProtectionOnboardingStateSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows defender advanced threat protection onboarding state summary across the account.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get advancedThreatProtectionOnboardingStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-advancedthreatprotectiononboardingstatesummary-get?view=graph-rest-beta) | [advancedThreatProtectionOnboardingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingstatesummary?view=graph-rest-beta) | Read properties and relationships of the [advancedThreatProtectionOnboardingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingstatesummary?view=graph-rest-beta) object. |
| [Update advancedThreatProtectionOnboardingStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-advancedthreatprotectiononboardingstatesummary-update?view=graph-rest-beta) | [advancedThreatProtectionOnboardingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingstatesummary?view=graph-rest-beta) | Update the properties of a [advancedThreatProtectionOnboardingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingstatesummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier |
| unknownDeviceCount | Int32 | Number of unknown devices |
| notApplicableDeviceCount | Int32 | Number of not applicable devices |
| compliantDeviceCount | Int32 | Number of compliant devices |
| remediatedDeviceCount | Int32 | Number of remediated devices |
| nonCompliantDeviceCount | Int32 | Number of NonCompliant devices |
| errorDeviceCount | Int32 | Number of error devices |
| conflictDeviceCount | Int32 | Number of conflict devices |
| notAssignedDeviceCount | Int32 | Number of not assigned devices |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| advancedThreatProtectionOnboardingDeviceSettingStates | [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta) collection |  |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.advancedThreatProtectionOnboardingStateSummary",
  "id": "String (identifier)",
  "unknownDeviceCount": 1024,
  "notApplicableDeviceCount": 1024,
  "compliantDeviceCount": 1024,
  "remediatedDeviceCount": 1024,
  "nonCompliantDeviceCount": 1024,
  "errorDeviceCount": 1024,
  "conflictDeviceCount": 1024,
  "notAssignedDeviceCount": 1024
}
```
