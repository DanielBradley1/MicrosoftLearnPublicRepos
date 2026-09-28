<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmobileappidentifier?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosMobileAppIdentifier resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The identifier for an iOS app.

Inherits from [mobileAppIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mobileappidentifier?view=graph-rest-1.0)

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
  "@odata.type": "#microsoft.graph.iosMobileAppIdentifier",
  "bundleId": "String"
}
```
