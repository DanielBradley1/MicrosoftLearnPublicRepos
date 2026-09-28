<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-additionaluseroptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-16 -->

# additionalUserOptions resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents additional configuration options for user provisioning and management in industry data synchronization scenarios. This resource provides settings that control how users, particularly students, are processed and configured during data synchronization operations.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowStudentContactAssociation | Boolean | Indicates whether student contact association should be allowed. |
| studentAgeGroup | microsoft.graph.industryData.studentAgeGroup | Indicates the age group classification for students. The possible values are: `minor`, `notAdult`, `adult`, `unknownFutureValue`. Use `null` to disable age group enforcement. |
| markAllStudentsAsMinors \(deprecated\) | Boolean | Indicates whether all students should be marked as minors. The **markAllStudentsAsMinors** property is deprecated and will stop returning data on October 15, 2025. Going forward, use the **studentAgeGroup** property. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.additionalUserOptions",
  "allowStudentContactAssociation": "Boolean",
  "markAllStudentsAsMinors": "Boolean",
  "studentAgeGroup": "String"
}
```
