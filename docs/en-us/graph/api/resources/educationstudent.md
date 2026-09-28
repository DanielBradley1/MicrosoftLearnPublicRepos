<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationstudent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# educationStudent resource type

Namespace: microsoft.graph

Additional information added to an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) that is present when the primaryRole of a user is `student`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| birthDate | Date | Birth date of the student. |
| externalId | String | ID of the student in the source system. |
| gender | educationGender | The possible values are: `female`, `male`, `other`, `unknownFutureValue`. |
| grade | String | Current grade level of the student. |
| graduationYear | String | Year the student is graduating from the school. |
| studentNumber | String | Student Number. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationStudent",
  "birthDate": "DateTimeOffset",
  "externalId": "String",
  "gender": "String",
  "grade": "String",
  "graduationYear": "String",
  "studentNumber": "String"
}
```
