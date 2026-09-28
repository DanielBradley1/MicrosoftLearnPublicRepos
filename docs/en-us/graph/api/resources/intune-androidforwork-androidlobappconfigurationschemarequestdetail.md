<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidlobappconfigurationschemarequestdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# androidLobAppConfigurationSchemaRequestDetail resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The request parameter for requesting Android LOB app configuration schema.

Inherits from [appConfigurationSchemaRequestDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-appconfigurationschemarequestdetail?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The application policy ID of the Android LOB app |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidLobAppConfigurationSchemaRequestDetail",
  "appId": "String"
}
```
