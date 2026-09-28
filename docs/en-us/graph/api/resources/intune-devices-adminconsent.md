<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-adminconsent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# adminConsent resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Admin consent information.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| shareAPNSData | [adminConsentState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-adminconsentstate?view=graph-rest-beta) | The admin consent state of sharing user and device data to Apple. Possible values are: `notConfigured`, `granted`, `notGranted`. |
| shareUserExperienceAnalyticsData | [adminConsentState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-adminconsentstate?view=graph-rest-beta) | Gets or sets the admin consent for sharing User experience analytics data. Possible values are: `notConfigured`, `granted`, `notGranted`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.adminConsent",
  "shareAPNSData": "String",
  "shareUserExperienceAnalyticsData": "String"
}
```
