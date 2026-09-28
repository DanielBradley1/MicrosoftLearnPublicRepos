<!-- Source: https://learn.microsoft.com/en-us/graph/api/corsconfiguration_v2-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-25 -->

# Update corsConfiguration\_v2

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /applications/{applicationObjectId}/onPremisesPublishing/segmentsConfiguration/microsoft.graph.webSegmentConfiguration/applicationSegments/{applicationSegment-id}/corsConfigurations/{corsConfiguration_v2-Id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedHeaders | String Collection | The request headers that the origin domain may specify on the CORS request. The wildcard character `*` indicates that any header beginning with the specified prefix is allowed. |
| allowedMethods | String Collection | The HTTP request methods that the origin domain may use for a CORS request. |
| allowedOrigins | String Collection | The origin domains that are permitted to make a request against the service via CORS. The origin domain is the domain from which the request originates. The origin must be an exact case-sensitive match with the origin that the user agent sends to the service. |
| maxAgeInSeconds | Integer | The maximum amount of time that a browser should cache the response to the preflight **OPTIONS** request. |
| resource | String | Resource within the application segment for which CORS permissions are granted. `/` grants permission for the whole app segment. |

## Response

If successful, this method returns a `200 OK` response code and an updated [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/beta/applications/{applicationObjectId}/onPremisesPublishing/segmentsConfiguration/microsoft.graph.webSegmentConfiguration/applicationSegments/{segmentid}/corsConfigurations/{id}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.corsConfiguration_v2",
  "resource": "/",
  "allowedOrigins": [
    ""
  ],
  "allowedHeaders": [
    ""
  ],
  "allowedMethods": [
    ""
  ],
  "maxAgeInSeconds": 3000
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const corsConfiguration_v2 = {
  '@odata.type': '#microsoft.graph.corsConfiguration_v2',
  resource: '/',
  allowedOrigins: [
    ''
  ],
  allowedHeaders: [
    ''
  ],
  allowedMethods: [
    ''
  ],
  maxAgeInSeconds: 3000
};

await client.api('/applications/{applicationObjectId}/onPremisesPublishing/segmentsConfiguration/microsoft.graph.webSegmentConfiguration/applicationSegments/{segmentid}/corsConfigurations/{id}')
	.version('beta')
	.update(corsConfiguration_v2);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
