<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-edgesearchengine?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# edgeSearchEngine resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Allows IT admins to set a predefined default search engine for MDM-Controlled devices.

Inherits from [edgeSearchEngineBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-edgesearchenginebase?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| edgeSearchEngineType | [edgeSearchEngineType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-edgesearchenginetype?view=graph-rest-1.0) | Allows IT admins to set a predefined default search engine for MDM-Controlled devices. The possible values are: `default`, `bing`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.edgeSearchEngine",
  "edgeSearchEngineType": "String"
}
```
