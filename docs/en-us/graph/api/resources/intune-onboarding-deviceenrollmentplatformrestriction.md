<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestriction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceEnrollmentPlatformRestriction resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Platform specific enrollment restrictions

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| platformBlocked | Boolean | Block the platform from enrolling |
| personalDeviceEnrollmentBlocked | Boolean | Block personally owned devices from enrolling |
| osMinimumVersion | String | Min OS version supported |
| osMaximumVersion | String | Max OS version supported |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceEnrollmentPlatformRestriction",
  "platformBlocked": true,
  "personalDeviceEnrollmentBlocked": true,
  "osMinimumVersion": "String",
  "osMaximumVersion": "String"
}
```
