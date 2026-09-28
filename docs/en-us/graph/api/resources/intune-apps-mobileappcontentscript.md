<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# mobileAppContentScript resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for a script associated with amobileLobApp entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppContentScripts](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontentscript-list?view=graph-rest-beta) | [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) collection | List properties and relationships of the [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) objects. |
| [Get mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontentscript-get?view=graph-rest-beta) | [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) | Read properties and relationships of the [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the script associated with a mobileLobApp entity. This property is read-only. |
| displayName | String | The display name for the script. |
| content | String | The content of the script. This is a Base64-encoded representation of the script's original content. The content has a maximum size limit of 100KB. |
| state | [mobileAppContentScriptState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscriptstate?view=graph-rest-beta) | Indicates the state of the script upload. Possible values are commitPending, commitSuccess, and commitFailed. This property is read-only. Possible values are: `commitPending`, `commitSuccess`, `commitFailed`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppContentScript",
  "id": "String (identifier)",
  "displayName": "String",
  "content": "String",
  "state": "String"
}
```
