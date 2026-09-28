<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recyclebinsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# recycleBinSettings resource type

Namespace: microsoft.graph

Represents settings for the [recycleBin](https://learn.microsoft.com/en-us/graph/api/resources/recyclebin?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| retentionPeriodOverrideDays | Int32 | Recycle bin retention period override in days for deleted content. The default value is `93`; the value range is `7` to `180`. The setting applies to newly deleted content only. Setting this property to `null` reverts to its default value. Read-write. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.recycleBinSettings",
  "retentionPeriodOverrideDays": "int32"
}
```
