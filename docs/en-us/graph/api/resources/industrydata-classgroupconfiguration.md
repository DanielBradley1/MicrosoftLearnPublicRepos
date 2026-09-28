<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-classgroupconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# classGroupConfiguration resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The different configurations choices for the class groups to be provisioned with.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalAttributes | microsoft.graph.industryData.additionalClassGroupAttributes collection | The different attributes to sync for the class groups. The possible values are: `courseTitle`, `courseCode`, `courseSubject`, `courseGradeLevel`, `courseExternalId`, `academicSessionTitle`, `academicSessionExternalId`, `classCode`, `unknownFutureValue`. |
| additionalOptions | [microsoft.graph.industryData.additionalClassGroupOptions](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-additionalclassgroupoptions?view=graph-rest-beta) | The different options for the class groups to be provisioned with. |
| enrollmentMappings | [microsoft.graph.industryData.enrollmentMappings](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-enrollmentmappings?view=graph-rest-beta) | The different enrollmentMappings for the class groups to be provisioned with. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.classGroupConfiguration",
  "additionalAttributes": ["String"],
  "additionalOptions": {
    "@odata.type": "microsoft.graph.industryData.additionalClassGroupOptions"
  },
  "enrollmentMappings": {
    "@odata.type": "microsoft.graph.industryData.enrollmentMappings"
  }
}
```
