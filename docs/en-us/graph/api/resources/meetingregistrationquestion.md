<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# meetingRegistrationQuestion resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a custom registration question, other than first name, last name, and email address, associated with a [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/meetingregistration-list-customquestions?view=graph-rest-beta) | [meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) collection | List all custom registration questions. |
| [Create](https://learn.microsoft.com/en-us/graph/api/meetingregistration-post-customquestions?view=graph-rest-beta) | [meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) | Create a custom registration question. |
| [Get](https://learn.microsoft.com/en-us/graph/api/meetingregistrationquestion-get?view=graph-rest-beta) | [meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) | Get a custom registration question. |
| [Update](https://learn.microsoft.com/en-us/graph/api/meetingregistrationquestion-update?view=graph-rest-beta) | [meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) | Update a custom registration question. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/meetingregistrationquestion-delete?view=graph-rest-beta) | [meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) | Delete a custom registration question. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| answerInputType | [answerInputType](#answerinputtype-values) | Answer input type of the custom registration question. |
| answerOptions | String collection | Answer options when **answerInputType** is `radioButton`. |
| displayName | String | Display name of the custom registration question. |
| id | String | ID of the custom registration question. Read-only. |
| isRequired | Boolean | Indicates whether the question is required. Default value is `false`. |

### answerInputType values

| Value | Description |
| --- | --- |
| text | Question accepts a single line text answer. |
| radioButton | Question accepts an answer chosen from radio buttons. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

```json
{
  "id": "String",
  "displayName": "String",
  "isRequired": "Boolean",
  "answerInputType": { "@odata.type": "microsoft.graph.answerInputType" },
  "answerOptions": [ "String" ],
}
```
