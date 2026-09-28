<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingenrollmenttypeconstraint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementSettingEnrollmentTypeConstraint resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Constraint that enforces the enrollment types applied to a setting

Inherits from [deviceManagementConstraint](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementconstraint?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enrollmentTypes | String collection | List of enrollment types |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementSettingEnrollmentTypeConstraint",
  "enrollmentTypes": [
    "String"
  ]
}
```
