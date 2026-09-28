<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# corsConfiguration resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the CORS settings \(**corsConfigurations** property\) for the [onPremisesApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesapplicationsegment?view=graph-rest-beta) resource when publishing an on-premises application through Microsoft Entra application proxy. For more information, see [Understand and solve Microsoft Entra application proxy CORS issues](https://learn.microsoft.com/en-us/azure/active-directory/app-proxy/application-proxy-understand-cors-issues).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedHeaders | String Collection | The request headers that the origin domain may specify on the CORS request. The wildcard character `*` indicates that any header beginning with the specified prefix is allowed. |
| allowedMethods | String Collection | The HTTP request methods that the origin domain may use for a CORS request. |
| allowedOrigins | String Collection | The origin domains that are permitted to make a request against the service via CORS. The origin domain is the domain from which the request originates. The origin must be an exact case-sensitive match with the origin that the user age sends to the service. |
| maxAgeInSeconds | Integer | The maximum amount of time that a browser should cache the response to the preflight **OPTIONS** request. |
| resource | String | Resource within the application segment for which CORS permissions are granted. `/` grants permission for whole app segment. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.corsConfiguration",
  "resource": "String",
  "allowedOrigins": [
    "String"
  ],
  "allowedHeaders": [
    "String"
  ],
  "allowedMethods": [
    "String"
  ],
  "maxAgeInSeconds": "Integer"
}
```
