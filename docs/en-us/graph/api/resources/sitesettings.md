<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sitesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# siteSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the settings of a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| languageTag | String | The language tag for the language used on this site. |
| timeZone | String | Indicates the time offset for the time zone of the site from Coordinated Universal Time \(UTC\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "languageTag": "String",
    "timeZone": "String"
}
```
