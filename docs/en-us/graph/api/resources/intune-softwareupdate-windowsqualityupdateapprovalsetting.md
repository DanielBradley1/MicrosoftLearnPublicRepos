<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateapprovalsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# windowsQualityUpdateApprovalSetting resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity to record approval settings for windows quality update policies

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| windowsQualityUpdateCadence | [windowsQualityUpdateCadence](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecadence?view=graph-rest-beta) | The publishing cadence of a quality update catalog item. Possible values are: `monthly`, `outOfBand`, `unknownFutureValue`. |
| windowsQualityUpdateCategory | [windowsQualityUpdateCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecategory?view=graph-rest-beta) | The category of a Windows quality update catalog item. Possible values are: `all`, `security`, `nonSecurity`, `unknownFutureValue`, `quickMachineRecovery`. |
| approvalMethodType | [windowsQualityUpdatePolicyApprovalMethodType](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyapprovalmethodtype?view=graph-rest-beta) | The approval type of specific gourp of quality updates. Possible values are: `manual`, `automatic`, `unknownFutureValue`. |
| deferredDeploymentInDay | Int32 | The deferral days for auto approval type, not applicable for manual approve |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsQualityUpdateApprovalSetting",
  "windowsQualityUpdateCadence": "String",
  "windowsQualityUpdateCategory": "String",
  "approvalMethodType": "String",
  "deferredDeploymentInDay": 1024
}
```
