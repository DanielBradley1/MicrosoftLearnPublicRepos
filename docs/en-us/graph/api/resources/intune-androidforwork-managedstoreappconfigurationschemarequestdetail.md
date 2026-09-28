<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-managedstoreappconfigurationschemarequestdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# managedStoreAppConfigurationSchemaRequestDetail resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The request parameter for requesting Android Managed Play Store app configuration schema.

Inherits from [appConfigurationSchemaRequestDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-appconfigurationschemarequestdetail?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| packageName | String | The package name of the Android Managed Play Store app |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedStoreAppConfigurationSchemaRequestDetail",
  "packageName": "String"
}
```
