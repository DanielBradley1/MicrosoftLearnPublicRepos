<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpc-rename?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# cloudPC: rename

Namespace: microsoft.graph

Rename a specific [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-1.0) object. Use this API to update the **displayName** of a Cloud PC entity.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

To rename the specified [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-1.0) in the organization, using either delegated permission \(the signed-in user should be the administrator\) or application permission:

```http
POST /deviceManagement/virtualEndpoint/cloudPCs/{cloudPCId}/rename
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameter that you can use with this action.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The new display name for the Cloud PC. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request to rename a Cloud PC for the administrator.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/cloudPCs/c2bbb5dd-2574-451b-a508-bbaa6ac48ace/rename
Content-Type: application/json

{
  displayName: "Cloud PC-HR"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const rename = {
  displayName: 'Cloud PC-HR'
};

await client.api('/deviceManagement/virtualEndpoint/cloudPCs/c2bbb5dd-2574-451b-a508-bbaa6ac48ace/rename')
	.post(rename);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
