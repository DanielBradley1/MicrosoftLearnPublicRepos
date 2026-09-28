<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sectiondisplayicon?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# sectionDisplayIcon resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the icon displayed for a [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in Microsoft Teams. The icon can be an emoji character or a custom image.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentUrl | String | The URL to a custom icon image. Applicable when **iconType** is `custom`. |
| displayName | String | The human-readable name of the icon. |
| iconType | String | The type of icon. Use an emoji character such as `👍` for an emoji icon, or `custom` for a custom image icon. |
| skinTone | sectionIconSkinTone | The skin tone variant applied to the icon. Read-only. The possible values are: `light`, `mediumLight`, `medium`, `mediumDark`, `dark`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sectionDisplayIcon",
  "contentUrl": "String",
  "displayName": "String",
  "iconType": "String",
  "skinTone": "String"
}
```

## Related content

- [teamworkSection resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta)
