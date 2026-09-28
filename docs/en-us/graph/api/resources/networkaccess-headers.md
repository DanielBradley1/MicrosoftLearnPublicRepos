<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-headers?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# headers resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The HTTP headers represent the additional information included in a network request or response. These headers contain various attributes and values that provide additional context or instructions for the communication between the client and the server.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| origin | String | Represents the origin or source from which the request is being made. |
| referrer | String | Represents the referring URL or the URL of the web page that the current request originates from. |
| xForwardedFor | String | Represents the information about the client original IP address when the request passes through one or more proxy servers or load balancers. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.headers",
  "referrer": "String",
  "origin": "String",
  "xForwardedFor": "String"
}
```
