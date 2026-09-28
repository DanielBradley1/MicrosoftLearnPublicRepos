<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# comanagementEligibleDevice resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Co-Management eligibility state

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List comanagementEligibleDevices](https://learn.microsoft.com/en-us/graph/api/intune-devices-comanagementeligibledevice-list?view=graph-rest-beta) | [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta) collection | List properties and relationships of the [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta) objects. |
| [Get comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-comanagementeligibledevice-get?view=graph-rest-beta) | [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta) | Read properties and relationships of the [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta) object. |
| [Create comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-comanagementeligibledevice-create?view=graph-rest-beta) | [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta) | Create a new [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta) object. |
| [Delete comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-comanagementeligibledevice-delete?view=graph-rest-beta) | None | Deletes a [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta). |
| [Update comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-comanagementeligibledevice-update?view=graph-rest-beta) | [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta) | Update the properties of a [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Id for the device |
| deviceName | String | DeviceName |
| deviceType | [deviceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicetype?view=graph-rest-beta) | DeviceType. Possible values are: `desktop`, `windowsRT`, `winMO6`, `nokia`, `windowsPhone`, `mac`, `winCE`, `winEmbedded`, `iPhone`, `iPad`, `iPod`, `android`, `iSocConsumer`, `unix`, `macMDM`, `holoLens`, `surfaceHub`, `androidForWork`, `androidEnterprise`, `windows10x`, `androidnGMS`, `chromeOS`, `linux`, `visionOS`, `tvOS`, `blackberry`, `palm`, `unknown`, `cloudPC`. |
| clientRegistrationStatus | [deviceRegistrationState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceregistrationstate?view=graph-rest-beta) | ClientRegistrationStatus. Possible values are: `notRegistered`, `registered`, `revoked`, `keyConflict`, `approvalPending`, `certificateReset`, `notRegisteredPendingEnrollment`, `unknown`. |
| ownerType | [ownerType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ownertype?view=graph-rest-beta) | OwnerType. Possible values are: `unknown`, `company`, `personal`. |
| managementAgents | [managementAgentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-managementagenttype?view=graph-rest-beta) | ManagementAgents. Possible values are: `eas`, `mdm`, `easMdm`, `intuneClient`, `easIntuneClient`, `configurationManagerClient`, `configurationManagerClientMdm`, `configurationManagerClientMdmEas`, `unknown`, `jamf`, `googleCloudDevicePolicyController`, `microsoft365ManagedMdm`, `msSense`, `intuneAosp`, `google`, `unknownFutureValue`. |
| managementState | [managementState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-managementstate?view=graph-rest-beta) | ManagementState. Possible values are: `managed`, `retirePending`, `retireFailed`, `wipePending`, `wipeFailed`, `unhealthy`, `deletePending`, `retireIssued`, `wipeIssued`, `wipeCanceled`, `retireCanceled`, `discovered`, `unknownFutureValue`. |
| referenceId | String | ReferenceId |
| mdmStatus | String | MDMStatus |
| osVersion | String | OSVersion |
| serialNumber | String | SerialNumber |
| manufacturer | String | Manufacturer |
| model | String | Model |
| osDescription | String | OSDescription |
| entitySource | Int32 | EntitySource |
| userId | String | UserId |
| upn | String | UPN |
| userEmail | String | UserEmail |
| userName | String | UserName |
| status | [comanagementEligibleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibletype?view=graph-rest-beta) | ComanagementEligibleStatus. Possible values are: `comanaged`, `eligible`, `eligibleButNotAzureAdJoined`, `needsOsUpdate`, `ineligible`, `scheduledForEnrollment`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.comanagementEligibleDevice",
  "id": "String (identifier)",
  "deviceName": "String",
  "deviceType": "String",
  "clientRegistrationStatus": "String",
  "ownerType": "String",
  "managementAgents": "String",
  "managementState": "String",
  "referenceId": "String",
  "mdmStatus": "String",
  "osVersion": "String",
  "serialNumber": "String",
  "manufacturer": "String",
  "model": "String",
  "osDescription": "String",
  "entitySource": 1024,
  "userId": "String",
  "upn": "String",
  "userEmail": "String",
  "userName": "String",
  "status": "String"
}
```
