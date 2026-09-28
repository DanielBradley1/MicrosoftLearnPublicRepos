<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-iosavailableupdateversion?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosAvailableUpdateVersion resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

iOS available update version details

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| productVersion | String | The version of the update. |
| postingDateTime | DateTimeOffset | The posting date of the update. |
| expirationDateTime | DateTimeOffset | The expiration date of the update. |
| supportedDevices | String collection | List of supported devices for the update. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosAvailableUpdateVersion",
  "productVersion": "String",
  "postingDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "supportedDevices": [
    "String"
  ]
}
```
