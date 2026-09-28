<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkhostedcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkHostedContent resource type

Namespace: microsoft.graph

Represents rich content like images and code snippets in Microsoft Teams. For rich content in [channel and chat messages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0), see [chatMessageHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehostedcontent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentBytes | Binary | Write only. Bytes for the hosted content \(such as images\). |
| contentType | String | Write only. Content type. such as image/png, image/jpg. |
| id | String | ID of the hosted content. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "contentBytes": "Binary",
  "contentType": "String"
}
```
