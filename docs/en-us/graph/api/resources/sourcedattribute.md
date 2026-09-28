<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sourcedattribute?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# sourcedAttribute resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An attribute specifying where the claim data is sourced.

Inherits from [customClaimAttributeBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimattributebase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the attribute on the specified source. |
| isExtensionAttribute | Boolean | A flag that indicates if the name specified is that of an extension attribute. |
| source | String | The source where the claim is going to retrieve its value. Valid sources include user, application, resource, audience and company. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sourcedAttribute",
  "id": "String",
  "source": "String",
  "isExtensionAttribute": "Boolean"
}
```
