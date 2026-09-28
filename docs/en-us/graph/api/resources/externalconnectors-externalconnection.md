<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-24 -->

# externalConnection resource type

Namespace: microsoft.graph.externalConnectors

A logical container to add content from an external source into Microsoft Graph.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create externalConnection](https://learn.microsoft.com/en-us/graph/api/externalconnectors-external-post-connections?view=graph-rest-1.0) | [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) | Create a new [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) object. |
| [List externalConnections](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-list?view=graph-rest-1.0) | [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) collection | Get a list of the [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) objects and their properties. |
| [Get externalConnection](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-get?view=graph-rest-1.0) | [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) | Read the properties and relationships of an [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) object. |
| [Update externalConnection](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-update?view=graph-rest-1.0) | [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) | Update the properties of an [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) object. |
| [Delete externalConnection](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-delete?view=graph-rest-1.0) | None | Deletes an [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) object. |
| [Create schema](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-patch-schema?view=graph-rest-1.0) | [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) | Create a new schema object. |
| [Create externalItem](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-put-items?view=graph-rest-1.0) | [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) | Create a new externalItem object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activitySettings | [microsoft.graph.externalConnectors.activitySettings](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-activitysettings?view=graph-rest-1.0) | Collects configurable settings related to activities involving connector content. |
| configuration | [microsoft.graph.externalConnectors.configuration](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-configuration?view=graph-rest-1.0) | Specifies additional application IDs that are allowed to manage the connection and to index content in the connection. Optional. |
| connectorId | String | The Teams app ID. Optional. |
| contentCategory | microsoft.graph.externalConnectors.contentCategory | Specifies the domain category of the content associated with the external connection. This property helps Microsoft Graph optimize relevance, ranking, and semantic understanding by signaling the nature of the ingested content. For example, setting this value correctly ensures better query interpretation and improves Copilot experiences. Possible values are: `uncategorized`, `knowledgeBase`, `wikis`, `fileRepository`, `qna`, `crm`, `dashboard`, `people`, `media`, `email`, `messaging`, `meetingTranscripts`, `taskManagement`, `learningManagement`, `unknownFutureValue`. Optional. The default value is `uncategorized`. |
| description | String | Description of the connection displayed in the Microsoft 365 admin center. Optional. |
| id | String | Developer-provided unique ID of the connection within the Microsoft Entra tenant. Must be between 3 and 32 characters in length. Must only contain alphanumeric characters. Cannot begin with `Microsoft` or be one of the following values: `None`, `Directory`, `Exchange`, `ExchangeArchive`, `LinkedIn`, `Mailbox`, `OneDriveBusiness`, `SharePoint`, `Teams`, `Yammer`, `Connectors`, `TaskFabric`, `PowerBI`, `Assistant`, `TopicEngine`, `MSFT_All_Connectors`. Required. |
| name | String | The display name of the connection to be displayed in the Microsoft 365 admin center. Maximum length of 128 characters. Required. |
| searchSettings | [microsoft.graph.externalConnectors.searchSettings](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-searchsettings?view=graph-rest-1.0) | The settings configuring the search experience for content in this connection, such as the display templates for search results. |
| state | microsoft.graph.externalConnectors.connectionState | Indicates the current state of the connection. The possible values are: `draft`, `ready`, `obsolete`, `limitExceeded`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| items | [microsoft.graph.externalConnectors.externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) collection | Read-only. Nullable. |
| operations | [microsoft.graph.externalConnectors.connectionOperation](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-connectionoperation?view=graph-rest-1.0) collection | Read-only. Nullable. |
| schema | [microsoft.graph.externalConnectors.schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "activitySettings": {
    "@odata.type": "microsoft.graph.externalConnectors.activitySettings"
  },
  "configuration": {
    "@odata.type": "microsoft.graph.externalConnectors.configuration"
  },
  "connectorId": "String",
  "description": "String",
  "id": "String (identifier)",
  "name": "String",
  "searchSettings": {
    "@odata.type": "microsoft.graph.externalConnectors.searchSettings"
  },
  "state": "String"
}
```
