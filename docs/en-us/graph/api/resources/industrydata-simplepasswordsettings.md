<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-simplepasswordsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# simplePasswordSettings resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The password settings for the users to be provisioned.

Inherits from [microsoft.graph.industryData.passwordSettings](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-passwordsettings?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| password | String | The password for the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.simplePasswordSettings",
  "password": "String"
}
```
