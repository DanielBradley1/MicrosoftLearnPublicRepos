<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usagerightsinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-12 -->

# usageRightsInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the detailed usage rights and permissions that a user has on content protected by a sensitivity label. This resource is based on Rights Management Services \(RMS\) usage rights evaluation and determines what actions the user can perform on the protected content.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowCopy | Boolean | Indicates whether the user has permission to copy content from the protected resource. When `true`, copying is allowed; when `false`, copying is restricted by the sensitivity label policy. |
| allowEdit | Boolean | Indicates whether the user has permission to edit or modify the protected content. When `true`, editing is allowed; when `false`, the content is read-only for this user. |
| allowExport | Boolean | Indicates whether the user has permission to export or save the protected content to external locations. When `true`, exporting is allowed; when `false`, export operations are restricted. |
| allowPrint | Boolean | Indicates whether the user has permission to print the protected content. When `true`, printing is allowed; when `false`, print functionality is disabled. |
| allowView | Boolean | Indicates whether the user has permission to view or access the protected content. When `true`, the user can view the content; when `false`, access is denied. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.usageRightsInfo",
  "allowCopy": "Boolean",
  "allowEdit": "Boolean",
  "allowExport": "Boolean",
  "allowPrint": "Boolean",
  "allowView": "Boolean"
}
```
