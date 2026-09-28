<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagecitation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# chatMessageCitation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an inline citation on a [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-beta) that references an external source. Bot-generated messages can include citations that point to source documents or web resources referenced in the message body. Citations are system-generated and read-only.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excerpt | String | Read-only. Text snippet from the cited source. |
| iconType | String | Read-only. Icon type identifier for the cited source, for example, `ExcelIcon` or `WordIcon`. |
| id | Int32 | Read-only. Citation identifier that's unique within the message. The message body references this identifier inline, for example, `[1]`. |
| sensitivityLabel | [chatMessageCitationSensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagecitationsensitivitylabel?view=graph-rest-beta) | Read-only. Sensitivity label applied to the cited source. |
| title | String | Read-only. Display title of the cited source. |
| webUrl | String | Read-only. URL to the cited source. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "excerpt": "String",
  "iconType": "String",
  "id": "Int32",
  "sensitivityLabel": {"@odata.type": "microsoft.graph.chatMessageCitationSensitivityLabel"},
  "title": "String",
  "webUrl": "String"
}
```
