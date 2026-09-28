<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-suggestedenrollmentlimit?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# suggestedEnrollmentLimit resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The suggestedEnrollmentLimit resource represents the suggested enrollment limit when given an enrollment type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| suggestedDailyLimit | Int32 | The suggested enrollment limit within a day |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.suggestedEnrollmentLimit",
  "suggestedDailyLimit": 1024
}
```
