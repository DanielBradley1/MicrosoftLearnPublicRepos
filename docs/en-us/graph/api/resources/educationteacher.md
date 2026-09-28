<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationteacher?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# Teacher resource type

Namespace: microsoft.graph

Additional information added to an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) that is present when the primaryRole of a user is `teacher`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalId | String | ID of the teacher in the source system. |
| teacherNumber | String | Teacher number. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationTeacher",
  "externalId": "String",
  "teacherNumber": "String"
}
```
