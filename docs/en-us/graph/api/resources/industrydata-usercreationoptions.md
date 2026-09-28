<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usercreationoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# userCreationOptions resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The different management choices for the users to be provisioned.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configurations | [microsoft.graph.industryData.userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-userconfiguration?view=graph-rest-beta) collection | The different management choices for the users to be provisioned. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.userCreationOptions",
  "configurations": [
    {
      "@odata.type": "microsoft.graph.industryData.userConfiguration"
    }
  ]
}
```
