<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentdefaults?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# educationAssignmentDefaults resource type

Namespace: microsoft.graph

Specifies class-level defaults respected by new assignments created in a class. Callers can continue to specify custom values on each assignment creation if they don't want the default behaviors.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationassignmentdefaults-get?view=graph-rest-1.0) | [educationAssignmentDefaults](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentdefaults?view=graph-rest-1.0) | Read the properties and relationships of an [educationAssignmentDefaults](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentdefaults?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/educationassignmentdefaults-update?view=graph-rest-1.0) | [educationAssignmentDefaults](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentdefaults?view=graph-rest-1.0) | Update the properties of an [educationAssignmentDefaults](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentdefaults?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addedStudentAction | educationAddedStudentAction | Class-level default behavior for handling students who are added after the assignment is published. The possible values are: `none`, `assignIfOpen`. |
| addToCalendarAction | educationAddToCalendarOptions | Optional field to control adding assignments to students' and teachers' calendars when the assignment is published. The possible values are: `none`, `studentsAndPublisher`, `studentsAndTeamOwners`, `unknownFutureValue`, and `studentsOnly`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `studentsOnly`. The default value is `none`. |
| dueTime | TimeOfDay | Class-level default value for due time field. Default value is `23:59:00`. |
| id | String | Unique identifier for the **educationAssignmentDefaults**. |
| notificationChannelUrl | String | Default Teams channel to which notifications are sent. Default value is `null`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "addedStudentAction": "String",
  "addToCalendarAction": "String",  
  "dueTime": "String (timestamp)",
  "id": "String (identifier)",
  "notificationChannelUrl": "String"
}
```
