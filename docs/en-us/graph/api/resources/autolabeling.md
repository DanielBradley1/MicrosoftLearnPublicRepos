<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/autolabeling?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-16 -->

# autoLabeling resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the configuration for automatically applying a sensitivity label based on detected sensitive information types.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| message | String | The message displayed to the user when the label is applied automatically. |
| sensitiveTypeIds | String collection | The list of sensitive information type \(SIT\) IDs that trigger the automatic application of this label. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.autoLabeling",
  "sensitiveTypeIds": [
    "String"
  ],
  "message": "String",
  "condition": "String"
}
```
