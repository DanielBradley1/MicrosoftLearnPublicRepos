<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-edgesearchenginecustom?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# edgeSearchEngineCustom resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Allows IT admins to set a custom default search engine for MDM-Controlled devices.

Inherits from [edgeSearchEngineBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-edgesearchenginebase?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| edgeSearchEngineOpenSearchXmlUrl | String | Points to a https link containing the OpenSearch xml file that contains, at minimum, the short name and the URL to the search Engine. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.edgeSearchEngineCustom",
  "edgeSearchEngineOpenSearchXmlUrl": "String"
}
```
