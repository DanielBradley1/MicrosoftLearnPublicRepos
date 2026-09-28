<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customappscopeattributesdictionary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-21 -->

# customAppScopeAttributesDictionary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a dictionary type that holds custom attributes for scope objects in different RBAC providers. The keys might vary based on the implementation from RBAC providers. Inherits from [Dictionary](https://learn.microsoft.com/en-us/graph/api/resources/dictionary?view=graph-rest-beta). Used by Exchange Online provider and Microsoft Defender XDR Unified RBAC provider.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| exclusive | Boolean | Indicates whether the object is an [exclusive scope](https://learn.microsoft.com/en-us/exchange/understanding-exclusive-scopes-exchange-2013-help). |
| recipientFilter | String | A filter query that defines how you segment your recipients that admins can manage. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customAppScopeAttributesDictionary",
  "exclusive": "Boolean",
  "recipientFilter": "String"
}
```
