<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagebody?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-25 -->

# chatMessageBody resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the content of a [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-beta) and the format of that content.

This type is specific to Teams messaging and supports additional content types, such as `markdown`, through the evolvable **chatMessageBodyContentType** enumeration. For general item bodies \(for example, mail and events\), use [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The content of the chat message. |
| contentType \(deprecated\) | bodyType | The type of the content. The possible values are: `text`, `html`. The **contentType** property is deprecated. Going forward, use the **messageBodyContentType** property. |
| messageBodyContentType | chatMessageBodyContentType | The type of the content, including support for additional Teams content types. The possible values are: `text`, `html`, `markdown`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "content": "String",
  "contentType": "String",
  "messageBodyContentType": "String"
}
```
