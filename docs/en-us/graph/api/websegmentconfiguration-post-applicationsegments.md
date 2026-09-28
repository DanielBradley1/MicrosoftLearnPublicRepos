<!-- Source: https://learn.microsoft.com/en-us/graph/api/websegmentconfiguration-post-applicationsegments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create webApplicationSegment

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) object.

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
POST /applications/{applicationObjectId}/onPremisesPublishing/segmentsConfiguration/microsoft.graph.webSegmentConfiguration/applicationSegments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) object.

You can specify the following properties when creating a **webApplicationSegment**.

| Property | Type | Description |
| :--- | :--- | :--- |
| alternateUrl | String | Optional. If you're configuring a traffic manager in front of multiple app proxy application segments, this property contains the user-friendly URL that points to the traffic manager. |
| externalUrl | String | Required. The published external URL for the application segment; for example, `https://intranet.contoso.com/`. |
| internalUrl | String | Required. The internal URL of the application segment; for example, `https://intranet/`. |
| corsConfigurations | [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) collection | Optional. A collection of CORS Rule definitions for a particular application segment. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/applications/2709c601-fcff-4010-94ea-5f862f755568/onPremisesPublishing/segmentsConfiguration/microsoft.graph.webSegmentConfiguration/applicationSegments/
Content-Type: application/json

{
    "externalUrl": "https://fe.contoso.com",
    "internalUrl": "https://be.contoso.com",
    "corsConfigurations": [
        {
            "resource": "/",
            "allowedOrigins": "*",
            "allowedHeaders": "*",
            "allowedMethods": "*",
            "maxAgeInSeconds": "3000"
        }
    ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const webApplicationSegment = {
    externalUrl: 'https://fe.contoso.com',
    internalUrl: 'https://be.contoso.com',
    corsConfigurations: [
        {
            resource: '/',
            allowedOrigins: '*',
            allowedHeaders: '*',
            allowedMethods: '*',
            maxAgeInSeconds: '3000'
        }
    ]
};

await client.api('/applications/2709c601-fcff-4010-94ea-5f862f755568/onPremisesPublishing/segmentsConfiguration/microsoft.graph.webSegmentConfiguration/applicationSegments/')
	.version('beta')
	.post(webApplicationSegment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
