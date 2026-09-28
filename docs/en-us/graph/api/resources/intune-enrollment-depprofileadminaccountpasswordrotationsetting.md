<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depprofileadminaccountpasswordrotationsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-09 -->

# depProfileAdminAccountPasswordRotationSetting resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Settings for local admin account password automatic rotation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| autoRotationPeriodInDays | Int32 | Indicates the number of days between 1-180 since the last rotation after which to rotate the local admin password. |
| depProfileDelayAutoRotationSetting | [depProfileDelayAutoRotationSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depprofiledelayautorotationsetting?view=graph-rest-beta) | Settings for delaying automatic password rotation upon retrieval. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.depProfileAdminAccountPasswordRotationSetting",
  "autoRotationPeriodInDays": 1024,
  "depProfileDelayAutoRotationSetting": {
    "@odata.type": "microsoft.graph.depProfileDelayAutoRotationSetting",
    "onRetrievalAutoRotatePasswordEnabled": true,
    "onRetrievalDelayAutoRotatePasswordInHours": 1024
  }
}
```
