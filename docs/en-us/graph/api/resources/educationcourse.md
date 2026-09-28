<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationcourse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# educationCourse resource type

Namespace: microsoft.graph

Represents the course information for a class. It is used within [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| courseNumber | String | Unique identifier for the course. |
| description | String | Description of the course. |
| displayName | String | Name of the course. |
| externalId | String | ID of the course from the syncing system. |
| subject | String | Subject of the course. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationCourse",
  "courseNumber": "String",
  "description": "String",
  "displayName": "String",
  "externalId": "String",
  "subject": "String"
}
```
