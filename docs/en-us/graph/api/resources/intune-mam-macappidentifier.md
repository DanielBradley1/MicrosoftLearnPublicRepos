<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-macappidentifier?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macAppIdentifier resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The identifier for a Mac app.

Inherits from [mobileAppIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mobileappidentifier?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bundleId | String | The identifier for an app, as specified in the app store. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macAppIdentifier",
  "bundleId": "String"
}
```
