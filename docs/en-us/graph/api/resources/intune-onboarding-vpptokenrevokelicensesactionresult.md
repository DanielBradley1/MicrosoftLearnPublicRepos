<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenrevokelicensesactionresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# vppTokenRevokeLicensesActionResult resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The status of the revoke licenses action performed on the Apple Volume Purchase Program token.

Inherits from [vppTokenActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenactionresult?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionName | String | Action name Inherited from [vppTokenActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenactionresult?view=graph-rest-beta) |
| actionState | [actionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-actionstate?view=graph-rest-beta) | State of the action Inherited from [vppTokenActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenactionresult?view=graph-rest-beta). Possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. |
| startDateTime | DateTimeOffset | Time the action was initiated Inherited from [vppTokenActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenactionresult?view=graph-rest-beta) |
| lastUpdatedDateTime | DateTimeOffset | Time the action state was last updated Inherited from [vppTokenActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenactionresult?view=graph-rest-beta) |
| totalLicensesCount | Int32 | A count of the number of licenses that were attempted to revoke. |
| failedLicensesCount | Int32 | A count of the number of licenses that failed to revoke. |
| actionFailureReason | [vppTokenActionFailureReason](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-vpptokenactionfailurereason?view=graph-rest-beta) | The reason for the revoke licenses action failure. Possible values are: `none`, `appleFailure`, `internalError`, `expiredVppToken`, `expiredApplePushNotificationCertificate`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vppTokenRevokeLicensesActionResult",
  "actionName": "String",
  "actionState": "String",
  "startDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)",
  "totalLicensesCount": 1024,
  "failedLicensesCount": 1024,
  "actionFailureReason": "String"
}
```
