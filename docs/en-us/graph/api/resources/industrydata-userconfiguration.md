<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-userconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# userConfiguration resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The different configurations choices for the users to be provisioned with.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultPasswordSettings | [microsoft.graph.industryData.passwordSettings](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-passwordsettings?view=graph-rest-beta) | The password settings for the users to be provisioned with. |
| licenseSkus | String collection | The license skus for the users to be provisioned with. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| roleGroup | [microsoft.graph.industryData.roleGroup](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta) | The role for the users to be provisioned with. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.userConfiguration",
  "defaultPasswordSettings": {
    "@odata.type": "microsoft.graph.industryData.passwordSettings"
  },
  "licenseSkus": ["String"]
}
```
