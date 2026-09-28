<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usermanagementoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# userManagementOptions resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The different configurations choices for the users to be provisioned.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalAttributes | microsoft.graph.industryData.additionalUserAttributes collection | The different attribute choices for the users to be provisioned. The possible values are: `userGradeLevel`, `userNumber`, `unknownFutureValue`. |
| additionalOptions | [microsoft.graph.industryData.additionalUserOptions](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-additionaluseroptions?view=graph-rest-beta) | The different management choices for the users to be provisioned. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.userManagementOptions",
  "additionalAttributes": ["String"],
  "additionalOptions": {
    "@odata.type": "microsoft.graph.industryData.additionalUserOptions"
  }
}
```
