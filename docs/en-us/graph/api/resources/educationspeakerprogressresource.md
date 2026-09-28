<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationspeakerprogressresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# educationSpeakerProgressResource resource type

Namespace: microsoft.graph

Represents a Speaker Progress resource that helps students develop confidence in their presentation skills and reduces anxiety. It provides AI-powered real-time coaching and feedback on their public speaking skills like their pace, pitch, filler words, and more.

Note

Getting the latest information for an **educationSpeakerProgressResource** requires the system to call an extra service. If that service is unavailable or no longer has a record for the requested **educationSpeakerProgressResource**, the system returns an object of `@odata.type #microsoft.graph.educationExternalResource` for read requests instead.

Inherits from [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aiFeedbackCriteria | [educationAiFeedbackCriteria](https://learn.microsoft.com/en-us/graph/api/resources/educationaifeedbackcriteria?view=graph-rest-1.0) | The feedback types that students should receive from AI feedback. This property should only be provided if **isAiFeedbackEnabled** is `true`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The individual who created the resource. Inherited from [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | Moment in time when the resource was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0). |
| displayName | String | Display name of resource. Inherited from [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0). |
| isAiFeedbackEnabled | Boolean | Indicates whether AI feedback is enabled for the student submissions. |
| isVideoRequired | Boolean | Indicates whether video is required for the student recording. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user to modify the resource. Inherited from [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | Moment in time when the resource was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0). |
| maxRecordingAttempts | Int32 | The maximum number of recording attempts available to the student. Specify `0` to set unlimited recording attempts. |
| presentationTitle | String | The title of the speaker progress resource visible to students. |
| recordingTimeLimitInMinutes | Int32 | The time limit is in minutes for the student recording. |
| showRehearsalReportToStudentBeforeMediaUpload | Boolean | Allows students to view their rehearsal report before the assignment is graded. |
| speakerCoachSettings | [educationSpeakerCoachSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationspeakercoachsettings?view=graph-rest-1.0) | The feedback types that students should receive from the Speaker Coach. |
| spokenLanguageLocale | String | The spoken language for the student recording. For example, `en-US`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationSpeakerProgressResource",
  "aiFeedbackCriteria": {"@odata.type": "microsoft.graph.educationAiFeedbackCriteria"},
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "isAiFeedbackEnabled": "Boolean",
  "isVideoRequired": "Boolean",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "maxRecordingAttempts": "Int32",
  "presentationTitle": "String",
  "recordingTimeLimitInMinutes": "Int32",
  "showRehearsalReportToStudentBeforeMediaUpload": "Boolean",
  "speakerCoachSettings": {"@odata.type": "microsoft.graph.educationSpeakerCoachSettings"},
  "spokenLanguageLocale": "String"
}
```
