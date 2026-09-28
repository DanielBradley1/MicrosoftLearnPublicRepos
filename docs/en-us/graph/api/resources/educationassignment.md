<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-18 -->

# educationAssignment resource type

Namespace: microsoft.graph

Represents a task or unit of work assigned to a student or team member in a class as part of their study.

**Assignments** contain handouts and tasks that the teacher wants the student to work on. Each student **assignment** has an associated [submission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) that contains any work their teacher asked to be turned in. Only teachers or team owners can create **assignments**. A teacher can add scores and feedback to the **submission** turned in by the student.

When an **assignment** is created, it is in a draft state. Students can't see the **assignment**, and **submissions** aren't created. You can change the status of an **assignment** by using the [publish](https://learn.microsoft.com/en-us/graph/api/educationassignment-publish?view=graph-rest-1.0) action. You can't use a PATCH request to change the **assignment** status.

The assignment APIs are exposed in the class namespace.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/educationclass-post-assignments?view=graph-rest-1.0) | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) | Create a new [assignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationassignment-get?view=graph-rest-1.0) | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) | Read properties and relationships of an **educationAssignment** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/educationassignment-update?view=graph-rest-1.0) | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) | Update an **educationAssignment** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/educationassignment-delete?view=graph-rest-1.0) | None | Delete an **educationAssignment** object. |
| [Publish](https://learn.microsoft.com/en-us/graph/api/educationassignment-publish?view=graph-rest-1.0) | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) | Change the state of an **educationAssignment** object from draft to published. |
| [Create assignment resource](https://learn.microsoft.com/en-us/graph/api/educationassignment-post-resources?view=graph-rest-1.0) | [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) | Create an [assignment resource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0). |
| [Get assignment resource](https://learn.microsoft.com/en-us/graph/api/educationassignmentresource-get?view=graph-rest-1.0) | [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) | Get the properties of an [education assignment resource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) associated with an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0). |
| [Delete assignment resource](https://learn.microsoft.com/en-us/graph/api/educationassignmentresource-delete?view=graph-rest-1.0) | None | Delete a specific [education assignment resource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) attached to an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0). |
| [Set up assignment resources folder](https://learn.microsoft.com/en-us/graph/api/educationassignment-setupresourcesfolder?view=graph-rest-1.0) | string | Create a SharePoint folder \(under predefined location\) to upload files as assignment resources. |
| [Set up assignment feedback resources folder](https://learn.microsoft.com/en-us/graph/api/educationassignment-setupfeedbackresourcesfolder?view=graph-rest-1.0) | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) | Create a SharePoint folder to upload feedback files for a given [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0). |
| [List resources](https://learn.microsoft.com/en-us/graph/api/educationassignment-list-resources?view=graph-rest-1.0) | [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) collection | Get an **educationAssignmentResource** object collection. |
| [List submissions](https://learn.microsoft.com/en-us/graph/api/educationassignment-list-submissions?view=graph-rest-1.0) | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) collection | Get an **educationSubmission** object collection. |
| [List categories](https://learn.microsoft.com/en-us/graph/api/educationassignment-list-categories?view=graph-rest-1.0) | [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0) collection | Get an **educationCategory** object collection. |
| [Add categories](https://learn.microsoft.com/en-us/graph/api/educationassignment-post-categories?view=graph-rest-1.0) | [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0) | Assign an **educationCategory** belonging to the class to this assignment. |
| [Remove category](https://learn.microsoft.com/en-us/graph/api/educationassignment-remove-category?view=graph-rest-1.0) | None | Remove an **educationCategory** belonging to the class from this assignment. |
| [Attach rubric](https://learn.microsoft.com/en-us/graph/api/educationassignment-put-rubric?view=graph-rest-1.0) | None | Attach an existing **educationRubric** to this assignment. |
| [Remove rubric](https://learn.microsoft.com/en-us/graph/api/educationassignment-delete-rubric?view=graph-rest-1.0) | None | Detach the **educationRubric** from this assignment. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/educationassignment-delta?view=graph-rest-1.0) | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) collection | Get a list of newly created or updated **educationAssignment** objects without having to perform a full read of the collection. |
| [Add grading category](https://learn.microsoft.com/en-us/graph/api/educationassignment-post-gradingcategory?view=graph-rest-1.0) | [educationGradingCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0) | Add a [gradingCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0) to an [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0). |
| [Remove grading category](https://learn.microsoft.com/en-us/graph/api/educationassignment-delete-gradingcategory?view=graph-rest-1.0) | None | Remove a [gradingCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0) from an [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0). |
| [Activate assignment](https://learn.microsoft.com/en-us/graph/api/educationassignment-activate?view=graph-rest-1.0) | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) | Activate an `inactive` **educationAssignment** to signal that the assignment has further action items for teachers or students. |
| [Deactivate assignment](https://learn.microsoft.com/en-us/graph/api/educationassignment-deactivate?view=graph-rest-1.0) | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) | Mark an `assigned` **educationAssignment** as `inactive` to signal that the assignment has no further action items for teachers and students. |
| [Add grading scheme](https://learn.microsoft.com/en-us/graph/api/educationassignment-put-gradingscheme?view=graph-rest-1.0) | [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) | Add an existing [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) to an existing [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addedStudentAction | String | Optional field to control the **assignment** behavior for students who are added after the **assignment** is published. If not specified, defaults to `none`. Supported values are: `none`, `assignIfOpen`. For example, a teacher can use `assignIfOpen` to indicate that an assignment should be assigned to any new student who joins the class while the assignment is still open, and `none` to indicate that an assignment shouldn't be assigned to new students. |
| addToCalendarAction | educationAddToCalendarOptions | Optional field to control the **assignment** behavior for adding **assignments** to students' and teachers' calendars when the **assignment** is published. The possible values are: `none`, `studentsAndPublisher`, `studentsAndTeamOwners`, `unknownFutureValue`, and `studentsOnly`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `studentsOnly`. The default value is `none`. |
| allowLateSubmissions | Boolean | Identifies whether students can submit after the due date. If this property isn't specified during create, it defaults to true. |
| allowStudentsToAddResourcesToSubmission | Boolean | Identifies whether students can add their own resources to a **submission** or if they can only modify resources added by the teacher. |
| assignDateTime | DateTimeOffset | The date when the **assignment** should become active. If in the future, the **assignment** isn't shown to the student until this date. The **Timestamp** type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| assignTo | [educationAssignmentRecipient](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentrecipient?view=graph-rest-1.0) | Which users, or whole class should receive a **submission** object once the **assignment** is published. |
| assignedDateTime | DateTimeOffset | The moment that the **assignment** was published to students and the **assignment** shows up on the students timeline. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| classId | String | Class to which this **assignment** belongs. |
| closeDateTime | DateTimeOffset | Date when the **assignment** is closed for **submissions**. This is an optional field that can be null if the **assignment** doesn't allowLateSubmissions or when the closeDateTime is the same as the dueDateTime. But if specified, then the closeDateTime must be greater than or equal to the dueDateTime. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Who created the **assignment**. |
| createdDateTime | DateTimeOffset | Moment when the **assignment** was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| displayName | String | Name of the **assignment**. |
| dueDateTime | DateTimeOffset | Date when the students **assignment** is due. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| feedbackResourcesFolderUrl | String | Folder URL where all the feedback file resources for this **assignment** are stored. |
| grading | [educationAssignmentGradeType](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentgradetype?view=graph-rest-1.0) | How the **assignment** will be graded. |
| id | String | The unique identifier for the **assignment**. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| instructions | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Instructions for the assignment. The instructions and the display name tell the student what to do. |
| languageTag | String | Specifies the language in which UI notifications for the assignment are displayed. If **languageTag** isn't provided, the default language is `en-US`. Optional. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Who last modified the **assignment**. |
| lastModifiedDateTime | DateTimeOffset | The date and time on which the **assignment** was modified. A student submission doesn't modify the assignment; only teachers can update assignments. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| moduleUrl | string | The URL of the module from which to access the **assignment**. |
| notificationChannelUrl | String | Optional field to specify the URL of the [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) to post the **assignment** publish notification. If not specified or null, defaults to the `General` channel. This field only applies to **assignments** where the **assignTo** value is [educationAssignmentClassRecipient](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentclassrecipient?view=graph-rest-1.0). Updating the **notificationChannelUrl** isn't allowed after the assignment is published. |
| resourcesFolderUrl | string | Folder URL where all the file resources for this **assignment** are stored. |
| status | educationAssignmentStatus | Status of the **assignment**. You can't PATCH this value. The possible values are: `draft`, `scheduled`, `published`, `assigned`, `unknownFutureValue`, `inactive`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `inactive`. |
| webUrl | string | The deep link URL for the given **assignment**. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0) collection | When set, enables users to easily find **assignments** of a given type. Read-only. Nullable. |
| gradingCategory | [educationGradingCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0) collection | When set, enables users to weight assignments differently when computing a class average grade. |
| gradingScheme | [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) | When set, enables users to configure custom string grades based on the percentage of total points earned on this **assignment**. |
| resources | [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) collection | Learning objects that are associated with this assignment. Only teachers can modify this list. Nullable. |
| rubric | [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) | When set, the grading rubric attached to this **assignment**. |
| submissions | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) collection | Once published, there's a **submission** object for each student representing their work and grade. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "addedStudentAction": "String",
  "addToCalendarAction": "String",  
  "allowLateSubmissions": "Boolean",
  "allowStudentsToAddResourcesToSubmission": "Boolean",
  "assignDateTime": "String (timestamp)",
  "assignTo": {"@odata.type": "microsoft.graph.educationAssignmentRecipient"},
  "assignedDateTime": "String (timestamp)",
  "classId": "String",
  "closeDateTime": "String (timestamp)",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "dueDateTime": "String (timestamp)",
  "feedbackResourcesFolderUrl": "String",
  "grading": {"@odata.type": "microsoft.graph.educationAssignmentGradeType"},
  "id": "String (identifier)",
  "instructions": {"@odata.type": "microsoft.graph.itemBody"},
  "languageTag": "String",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "moduleUrl": "String",
  "notificationChannelUrl": "String",
  "resourcesFolderUrl": "String",
  "status": "String",  
  "webUrl": "String"
}
```
