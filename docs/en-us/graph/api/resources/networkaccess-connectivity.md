<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connectivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-27 -->

# connectivity resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents all the connectivity components in Global Secure Access services.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get web category by URL](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-getwebcategorybyurl?view=graph-rest-beta) | [microsoft.graph.networkaccess.webCategory](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategory?view=graph-rest-beta) | Check the web category of a given Uniform Resource Locator \(URL\). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for this resource. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| webCategories | [microsoft.graph.networkaccess.webCategory](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategory?view=graph-rest-beta) collection | The URL category. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| branches | [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) collection | The locations for connectivity. **DEPRECATED AND TO BE RETIRED SOON. Use the remoteNetwork relationship and its associated APIs instead.** |
| remoteNetworks | [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) collection | The locations, such as branches, that are connected to Global Secure Access services through an IPsec tunnel. |

## JSON representation

Here's is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.connectivity",
  "id": "String (identifier)", 
  "webCategories": [
    {
      "@odata.type": "microsoft.graph.networkaccess.webCategory"
    }
  ]
}
```
