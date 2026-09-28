<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customquestionanswer?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# customQuestionAnswer resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a registrant's answer to the [custom registration question](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) associated with a [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the custom registration question. Read-only. |
| questionId | String | ID the custom registration question. Read-only. |
| value | String | Answer to the custom registration question. |

## Relationships

None.

## JSON representation

```json
{
  "id": "String",
  "displayName": "String",
  "value": "String"
}
```
