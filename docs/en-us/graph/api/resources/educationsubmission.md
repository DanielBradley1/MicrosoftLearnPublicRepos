<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# educationSubmission resource type

Namespace: microsoft.graph

Represents the resources that an individual \(or group\) turn in for an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) and the outcomes \(such as grades or feedback\) that are associated with the **submission**.

Submissions are owned by an **assignment**. Submissions are automatically created when an **assignment** is published. The **submission** owns two lists of resources. Resources represent the user/groups working area while the submitted resources represent the resources that have actively been turned in by students.

The **status** property is read-only and the object is moved through the workflow via actions.

If [setUpResourcesFolder](https://learn.microsoft.com/en-us/graph/api/educationsubmission-setupresourcesfolder?view=graph-rest-1.0) hasn't been called on an **educationSubmission** resource, the **resourcesFolderUrl** property is `null`.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get submission](https://learn.microsoft.com/en-us/graph/api/educationsubmission-get?view=graph-rest-1.0) | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) | Read properties and relationships of an **educationSubmission** object. |
| [List submission resources](https://learn.microsoft.com/en-us/graph/api/educationsubmission-list-resources?view=graph-rest-1.0) | [educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) collection | Get an **educationSubmissionResource** object collection. |
| [List submitted resources](https://learn.microsoft.com/en-us/graph/api/educationsubmission-list-submittedresources?view=graph-rest-1.0) | [educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) collection | Get an **educationSubmissionResource** object collection. |
| [List outcomes](https://learn.microsoft.com/en-us/graph/api/educationsubmission-list-outcomes?view=graph-rest-1.0) | [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) collection | Get an **educationOutcome** object collection. |
| [Excuse submission](https://learn.microsoft.com/en-us/graph/api/educationsubmission-excuse?view=graph-rest-1.0) | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) | Indicates that the submission has no further action for the student and isn't included in average grade calculations. |
| [Return submission](https://learn.microsoft.com/en-us/graph/api/educationsubmission-return?view=graph-rest-1.0) | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) | A teacher uses return to indicate that the grades/feedback can be shown to the student. |
| [Reassign submission](https://learn.microsoft.com/en-us/graph/api/educationsubmission-reassign?view=graph-rest-1.0) | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) | Reassign the submission to the student with feedback for review. |
| [Set up submission resources folder](https://learn.microsoft.com/en-us/graph/api/educationsubmission-setupresourcesfolder?view=graph-rest-1.0) | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) | Create a SharePoint folder \(under predefined location\) to upload files as submission resources. |
| [Submit submission](https://learn.microsoft.com/en-us/graph/api/educationsubmission-submit?view=graph-rest-1.0) | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) | A student uses submit to turn in the **assignment**. This operation copies the resources into the **submittedResources** folder for grading and updates the status. |
| [Unsubmit submission](https://learn.microsoft.com/en-us/graph/api/educationsubmission-unsubmit?view=graph-rest-1.0) | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) | A student uses the unsubmit to move the state of the submission from submitted back to working. This operation copies the resources into the **workingResources** folder for grading and updates the status. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentId | String | The unique identifier for the assignment with which this submission is associated. A submission is always associated with one and only one assignment. |
| excusedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user that marked the submission as excused. |
| excusedDateTime | DateTimeOffset | The time that the submission was excused. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | Unique identifier for the submission. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identities of those who modified the submission. |
| lastModifiedDateTime | DateTimeOffset | The date and time the submission was modified. |
| reassignedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | User who moved the status of this submission to reassigned. |
| reassignedDateTime | DateTimeOffset | Moment in time when the submission was reassigned. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| recipient | [educationSubmissionRecipient](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionrecipient?view=graph-rest-1.0) | Who this submission is assigned to. |
| resourcesFolderUrl | String | Folder where all file resources for this submission need to be stored. |
| returnedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | User who moved the status of this submission to returned. |
| returnedDateTime | DateTimeOffset | Moment in time when the submission was returned. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| status | educationSubmissionStatus | Read-only. The possible values are: `excused`, `reassigned`, `returned`, `submitted` and `working`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `excused` and `reassigned`. |
| submittedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | User who moved the resource into the submitted state. |
| submittedDateTime | DateTimeOffset | Moment in time when the submission was moved into the submitted state. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| unsubmittedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | User who moved the resource from submitted into the working state. |
| unsubmittedDateTime | DateTimeOffset | Moment in time when the submission was moved from submitted into the working state. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| webUrl | String | The deep link URL for the given submission. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| outcomes | [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) collection. Holds grades, feedback and/or rubrics information the teacher assigns to this submission | Read-Write. Nullable. |
| resources | [educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) collection | Nullable. |
| submittedResources | [educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) collection | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assignmentId": "String",
  "excusedBy": {"@odata.type":"microsoft.graph.identitySet"},
  "excusedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "reassignedBy": {"@odata.type":"microsoft.graph.identitySet"},
  "reassignedDateTime": "String (timestamp)",
  "recipient": {"@odata.type":"microsoft.graph.educationSubmissionRecipient"},
  "resourcesFolderUrl": "String",
  "returnedBy": {"@odata.type":"microsoft.graph.identitySet"},
  "returnedDateTime": "String (timestamp)",
  "status": "String",
  "submittedBy": {"@odata.type":"microsoft.graph.identitySet"},
  "submittedDateTime": "String (timestamp)",
  "unsubmittedBy": {"@odata.type":"microsoft.graph.identitySet"},
  "unsubmittedDateTime": "String (timestamp)",
  "webUrl": "String"
}
```
