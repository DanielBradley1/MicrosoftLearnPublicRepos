<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharinglinkexpirationstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# sharingLinkExpirationStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates whether links must expire, and if link expiration is enabled, provides a default link expiration time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultExpirationInDays | Int32 | Default link expiration in days. Returns -1 if there is no required expiration time. |
| disabledReason | String | Provides a description of why this operation is not enabled. Only returned if this operation is not enabled. |
| enabled | Boolean | Indicates whether this operation is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharingLinkExpirationStatus",
  "enabled": "Boolean",
  "disabledReason": "String",
  "defaultExpirationInDays": "Integer"
}
```
