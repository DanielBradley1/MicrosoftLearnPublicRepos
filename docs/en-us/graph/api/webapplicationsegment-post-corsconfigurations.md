<!-- Source: https://learn.microsoft.com/en-us/graph/api/webapplicationsegment-post-corsconfigurations?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-25 -->

# Create corsConfiguration\_v2

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

- *Application Administrator* is the least privileged role supported for this operation.
- *Cloud Application Administrator* can't manage app proxy settings.

## HTTP request

```http
POST /applications/{applicationObjectId}/onPremisesPublishing/segmentsConfiguration/microsoft.graph.webSegmentConfiguration/applicationSegments/{webApplicationSegment-id}/corsConfigurations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) object.

You can specify the following properties when creating a **corsConfiguration\_v2**.

| Property | Type | Description |
| :--- | :--- | :--- |
| resource | String | Resource within the application segment for which CORS permissions are granted. `/` grants permission for the whole app segment. Required. |
| allowedOrigins | String collection | The origin domains that are permitted to make a request against the service via CORS. The origin domain is the domain from which the request originates. The origin must be an exact case-sensitive match with the origin that the user agent sends to the service. Optional. |
| allowedHeaders | String collection | The request headers that the origin domain may specify on the CORS request. The wildcard character `*` indicates that any header beginning with the specified prefix is allowed. Optional. |
| allowedMethods | String collection | The HTTP request methods that the origin domain may use for a CORS request. Optional. |
| maxAgeInSeconds | Int32 | The maximum amount of time that a browser should cache the response to the preflight **OPTIONS** request. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/applications/129d6e80-484f-4d1f-bfca-a6a859d138ac/onPremisesPublishing/segmentsConfiguration/microsoft.graph.webSegmentConfiguration/ApplicationSegments/209efffb-0777-42b0-a65c-4e3ddb1ab3c0/corsConfigurations
Content-Type: application/json

{
  "allowedOrigins":[""],
  "allowedHeaders":[""],
  "allowedMethods":["*"],
  "maxAgeInSeconds":3000,
  "resource":"/"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const corsConfiguration_v2 = {
  allowedOrigins: [''],
  allowedHeaders: [''],
  allowedMethods: ['*'],
  maxAgeInSeconds: 3000,
  resource: '/'
};

await client.api('/applications/129d6e80-484f-4d1f-bfca-a6a859d138ac/onPremisesPublishing/segmentsConfiguration/microsoft.graph.webSegmentConfiguration/ApplicationSegments/209efffb-0777-42b0-a65c-4e3ddb1ab3c0/corsConfigurations')
	.version('beta')
	.post(corsConfiguration_v2);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "allowedOrigins":[""],
  "allowedHeaders":[""],
  "allowedMethods":["*"],
  "maxAgeInSeconds":3000,
  "resource":"/"
}
```
