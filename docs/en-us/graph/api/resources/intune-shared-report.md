<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-report?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# report resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Returns the content appropriate for the context, including:

- Device Configuration profile history reports.
- Enrollment failure reports.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | Report content; details vary by report type. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.report",
  "content": "<Unknown Primitive Type Edm.Stream>"
}
```
