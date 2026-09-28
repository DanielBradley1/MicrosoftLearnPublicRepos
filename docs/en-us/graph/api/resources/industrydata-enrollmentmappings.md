<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-enrollmentmappings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# enrollmentMappings resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The different management choices for the class groups to be provisioned.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| memberEnrollmentMappings | [microsoft.graph.industryData.sectionRoleReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sectionrolereferencevalue?view=graph-rest-beta) collection | The enrollmentMappings member for the class group. |
| ownerEnrollmentMappings | [microsoft.graph.industryData.sectionRoleReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sectionrolereferencevalue?view=graph-rest-beta) collection | The enrollmentMappings owner for the class group. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.enrollmentMappings",
  "ownerEnrollmentMappings": [
    {
      "@odata.type": "microsoft.graph.industryData.sectionRoleReferenceValue"
    }
  ],
  "memberEnrollmentMappings": [
    {
      "@odata.type": "microsoft.graph.industryData.sectionRoleReferenceValue"
    }
  ]
}
```
