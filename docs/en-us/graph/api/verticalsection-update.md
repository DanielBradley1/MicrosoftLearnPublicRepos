<!-- Source: https://learn.microsoft.com/en-us/graph/api/verticalsection-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Update verticalSection

Namespace: microsoft.graph

Update the properties of a [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) object.

If the vertical section doesn't exist, this method returns a `404 NotFound` response code.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/canvasLayout/verticalSection
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) resource to update.

## Response

If successful, this method returns a `200 OK` response code and an updated [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) object in the response body.

If the vertical section doesn't exist, this method returns a `404 NotFound` response code.

## Examples

### Request

The following is an example of a request.

```http
PATCH /sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage/canvasLayout/verticalSection
Content-Type: application/json

{
  "emphasis": "strong"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "emphasis": "strong",
  "webparts":[
    {
      "id":"20a69b85-529c-41f3-850e-c93458aa74eb",
      "innerHtml":"<p>sample text in text web part</p>"
    }
  ]
}
```
