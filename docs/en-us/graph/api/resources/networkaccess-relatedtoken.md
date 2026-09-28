<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedtoken?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# relatedToken resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a token involved in a Global Secure Access [alert](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alert?view=graph-rest-beta).

Inherits from [microsoft.graph.networkaccess.relatedResource](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedresource?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| uniqueTokenIdentifier | String | Unique identifier of the token. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.relatedToken",
  "uniqueTokenIdentifier": "String"
}
```
