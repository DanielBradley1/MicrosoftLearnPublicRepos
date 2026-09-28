<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-crosscloudgovernmentorganizationmapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create cloudPcCrossCloudGovernmentOrganizationMapping

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [cloudPcCrossCloudGovernmentOrganizationMapping](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccrosscloudgovernmentorganizationmapping?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/crossCloudGovernmentOrganizationMapping
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| X-MS-CloudPC-USGovCloudTenantAADToken | {token}. Required. Represents the Microsoft Entra token of the government cloud tenant. |

## Request body

The request body is an empty JSON string.

## Response

If successful, this method returns a `200 OK` response code and a [cloudPcCrossCloudGovernmentOrganizationMapping](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccrosscloudgovernmentorganizationmapping?view=graph-rest-beta) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/crossCloudGovernmentOrganizationMapping
Content-Type: application/json
X-MS-CloudPC-USGovCloudTenantAADToken: {token}

{}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcCrossCloudGovernmentOrganizationMapping = {};

await client.api('/deviceManagement/virtualEndpoint/crossCloudGovernmentOrganizationMapping')
	.version('beta')
	.post(cloudPcCrossCloudGovernmentOrganizationMapping);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcCrossCloudGovernmentOrganizationMapping",
  "id": "7e6e7d5b-8dd5-5078-16cf-d1e488be48a8",
  "organizationIdsInUSGovCloud": [
    "String"
  ]
}
```
