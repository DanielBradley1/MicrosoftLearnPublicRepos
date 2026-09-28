<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleownertypeenrollmenttype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# appleOwnerTypeEnrollmentType resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ownerType | [managedDeviceOwnerType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-manageddeviceownertype?view=graph-rest-beta) | The owner type. Possible values are: `unknown`, `company`, `personal`. |
| enrollmentType | [appleUserInitiatedEnrollmentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmenttype?view=graph-rest-beta) | The enrollment type. Possible values are: `unknown`, `device`, `user`, `accountDrivenUserEnrollment`, `webDeviceEnrollment`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.appleOwnerTypeEnrollmentType",
  "ownerType": "String",
  "enrollmentType": "String"
}
```
