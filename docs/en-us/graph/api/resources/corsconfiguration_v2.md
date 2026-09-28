<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-23 -->

# corsConfiguration\_v2 resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the CORS settings for the [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) resource when publishing an on-premises application through Microsoft Entra application proxy.For more information, see [Understand and solve Microsoft Entra application proxy CORS issues](https://learn.microsoft.com/en-us/azure/active-directory/app-proxy/application-proxy-understand-cors-issues).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/webapplicationsegment-list-corsconfigurations?view=graph-rest-beta) | [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) collection | Get a list of the [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/webapplicationsegment-post-corsconfigurations?view=graph-rest-beta) | [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) | Create a new [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/corsconfiguration_v2-get?view=graph-rest-beta) | [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) | Read the properties and relationships of a [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/corsconfiguration_v2-update?view=graph-rest-beta) | [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) | Update the properties of a [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/webapplicationsegment-delete-corsconfigurations?view=graph-rest-beta) | None | Delete a [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedHeaders | String Collection | The request headers that the origin domain may specify on the CORS request. The wildcard character `*` indicates that any header beginning with the specified prefix is allowed. |
| allowedMethods | String Collection | The HTTP request methods that the origin domain may use for a CORS request. |
| allowedOrigins | String Collection | The origin domains that are permitted to make a request against the service via CORS. The origin domain is the domain from which the request originates. The origin must be an exact case-sensitive match with the origin that the user agent sends to the service. |
| id | String | The unique identifier for the CORS configuration that is assigned to a CORS rule by Microsoft Entra ID. Not nullable. Read-only. Supports `$filter` \(`eq`\). |
| maxAgeInSeconds | Integer | The maximum amount of time that a browser should cache the response to the preflight **OPTIONS** request. |
| resource | String | Resource within the application segment for which CORS permissions are granted. `/` grants permission for the whole app segment. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "microsoft.graph.corsConfiguration_v2",
  "allowedHeaders": [
    "String"
  ],
  "allowedMethods": [
    "String"
  ],
  "allowedOrigins": [
    "String"
  ],
  "id": "String (identifier)",
  "maxAgeInSeconds": "Integer",
  "resource": "String"
}
```
