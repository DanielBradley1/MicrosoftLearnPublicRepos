<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# applicableContent resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents content applicable for offering to the related collection of devices.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List applicable content](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-list-applicablecontent?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontent?view=graph-rest-beta) collection | List [applicable update content](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontent?view=graph-rest-beta) to offer to Microsoft Entra groups, Windows Autopatch groups, or both. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| catalogEntryId | String | ID of the catalog entry for the applicable content. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| catalogEntry | [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta) | Catalog entry for the update or content. |
| matchedDevices | [microsoft.graph.windowsUpdates.applicableContentDeviceMatch](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontentdevicematch?view=graph-rest-beta) collection | Collection of devices and recommendations for applicable catalog content. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.applicableContent",
  "catalogEntryId": "String (identifier)"
}
```
