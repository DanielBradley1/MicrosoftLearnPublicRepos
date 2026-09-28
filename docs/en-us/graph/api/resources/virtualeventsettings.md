<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-07 -->

# virtualEventSettings resource type

Namespace: microsoft.graph

Represents the settings for a [virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isAttendeeEmailNotificationEnabled | Boolean | Indicates whether virtual event attendees receive email notifications. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| virtualEvents | [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0) | Provides configuration settings for a [virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventSettings",
  "isAttendeeEmailNotificationEnabled": "Boolean"
}
```

## Related content

- [Virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0)
- [Virtual event webinars](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0)
