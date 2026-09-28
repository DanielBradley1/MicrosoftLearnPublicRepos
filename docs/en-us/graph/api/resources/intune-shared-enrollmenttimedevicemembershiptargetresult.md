<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmenttimedevicemembershiptargetresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# enrollmentTimeDeviceMembershipTargetResult resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The EnrollmentTimeDeviceMembershipTargetResult entity represents the results of the set/get EnrollmentTimeDeviceMembershipTarget request. The set/get EnrollmentTimeDeviceMembershipTarget API validates the device membership targets specified by the admin to ensure that they exist, that they are of the proper type, and any other target requirements are met such as that the Intune Device Provisioning First Party App is an owner of the target. Failures other than validation will result in 500 else validationSucceeded will be true or false if any of the validation fails for EnrollmentTimeDeviceMembershipTarget.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| validationSucceeded | Boolean | Indicates if validations succeeded for the device membership target. When 'true', the device membership target validation found no issues. When 'false', the device membership target validation found issues. default - false |
| enrollmentTimeDeviceMembershipTargetValidationStatuses | [enrollmentTimeDeviceMembershipTargetStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmenttimedevicemembershiptargetstatus?view=graph-rest-beta) collection | A list of validation status of the memberships targetted to profile. This collection can contain a maximum of 1 elements. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.enrollmentTimeDeviceMembershipTargetResult",
  "validationSucceeded": true,
  "enrollmentTimeDeviceMembershipTargetValidationStatuses": [
    {
      "@odata.type": "microsoft.graph.enrollmentTimeDeviceMembershipTargetStatus",
      "targetId": "String",
      "validationSucceeded": true,
      "targetValidationErrorCode": "String"
    }
  ]
}
```
