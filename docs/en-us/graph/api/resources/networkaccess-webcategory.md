<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# webCategory resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the category or type of a website or online resource, helping to classify and filter internet traffic based on content.

Inherits from [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name for the web category. |
| group | String | The group or category to which the web category belongs. |
| name | String | The unique name that is associated with the web category. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webCategory",
  "displayName": "String",
  "name": "String",
  "group": "String"
}
```
