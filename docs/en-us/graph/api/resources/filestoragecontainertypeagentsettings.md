<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeagentsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-04 -->

# fileStorageContainerTypeAgentSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the settings for agents on a SharePoint Embedded application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| chatEmbedAllowedHosts | String collection | Determines which host URLs are allowed to embed the agent chat experience. Limited to 10 hosts. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fileStorageContainerTypeAgentSettings",
  "chatEmbedAllowedHosts": [
    "String"
  ]
}
```
