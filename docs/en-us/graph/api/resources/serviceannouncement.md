<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# serviceAnnouncement resource type

Namespace: microsoft.graph

A top-level container for service communications resources.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List health overviews](https://learn.microsoft.com/en-us/graph/api/serviceannouncement-list-healthoverviews?view=graph-rest-1.0) | [serviceHealth](https://learn.microsoft.com/en-us/graph/api/resources/servicehealth?view=graph-rest-1.0) collection | Get the serviceHealth resources from the healthOverviews navigation property. |
| [List issues](https://learn.microsoft.com/en-us/graph/api/serviceannouncement-list-issues?view=graph-rest-1.0) | [serviceHealthIssue](https://learn.microsoft.com/en-us/graph/api/resources/servicehealthissue?view=graph-rest-1.0) collection | Get the serviceHealthIssue resources from the issues navigation property. |
| [List messages](https://learn.microsoft.com/en-us/graph/api/serviceannouncement-list-messages?view=graph-rest-1.0) | [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0) collection | Get the serviceUpdateMessage resources from the messages navigation property. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| --- | --- | --- |
| healthOverviews | Collection\([serviceHealth](https://learn.microsoft.com/en-us/graph/api/resources/servicehealth?view=graph-rest-1.0)\) | A collection of service health information for tenant. This property is a contained navigation property, it is nullable and read-only. |
| issues | Collection\([serviceHealthIssue](https://learn.microsoft.com/en-us/graph/api/resources/servicehealthissue?view=graph-rest-1.0)\) | A collection of service issues for tenant. This property is a contained navigation property, it is nullable and read-only. |
| messages | Collection\([serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0)\) | A collection of service messages for tenant. This property is a contained navigation property, it is nullable and read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceAnnouncement"
}
```
