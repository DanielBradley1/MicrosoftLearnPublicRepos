<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-productrevision?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# productRevision resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a product revision that is associated with a quality update.

When a quality update is released, it includes one or more product revisions to operating system builds. The taxonomy of a product revision is `majorVersion.minorVersion.buildNumber.updateBuildRevision`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the content. Read-only. |
| id | String | The unique identifier for the product revision. Read-only. |
| isHotpatchUpdate | Boolean | `True` indicates that the content is hotpatchable; otherwise, `false`. For more information, see [Deploy a hotpatch quality update](https://learn.microsoft.com/en-us/graph/windowsupdates-hotpatch-update) using Windows Autopatch. Read-only. |
| osBuild | [microsoft.graph.windowsUpdates.buildVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-buildversiondetails?view=graph-rest-beta) | The version details of the product revision. Read-only. |
| product | String | The product of the revision. The possible values are: `Windows 10`, `Windows 11`. Read-only. |
| releaseDateTime | DateTimeOffset | The release date for the content. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| version | String | The version of the feature update. Read-only. |

## Relationships

| Property | Type | Description |
| :--- | :--- | :--- |
| knowledgeBaseArticle | [microsoft.graph.windowsUpdates.knowledgeBaseArticle](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-knowledgebasearticle?view=graph-rest-beta) | The knowledge base article associated with the product revision. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.productRevision",
  "displayName": "String",
  "id": "String (identifier)",
  "isHotpatchUpdate": "Boolean",
  "osBuild": { "@odata.type": "microsoft.graph.windowsUpdates.buildVersionDetails" },
  "product": "String",
  "releaseDateTime": "String (timestamp)",
  "version": "String"
}
```
