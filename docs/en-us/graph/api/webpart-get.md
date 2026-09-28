<!-- Source: https://learn.microsoft.com/en-us/graph/api/webpart-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Get webPart

Namespace: microsoft.graph

Read the properties and relationships of a [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Read.All | Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Read.All | Sites.ReadWrite.All |

## HTTP request

```http
GET /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/webParts/{webpart-id}
GET /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/canvasLayout/verticalSection/webparts/{webpart-index}
GET /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/canvasLayout/horizontalSections/{horizontal-section-id}/columns/{horizontal-section-column-id}/webparts/{webpart-index}
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [standardWebPart](https://learn.microsoft.com/en-us/graph/api/resources/standardwebpart?view=graph-rest-1.0) or [textWebPart](https://learn.microsoft.com/en-us/graph/api/resources/textwebpart?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get a webPart object

#### Request

The following is an example of a request.

```http
GET https://graph.microsoft.com/v1.0/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage/webParts/58ce69a6-bcb0-4f35-b6cd-d757d95f1a8e
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.textWebPart",
    "id": "1212fc8d-dd6b-408a-8d5d-9f1cc787efbb",
    "innerHtml": "<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque vel.</p>"
  }
}
```

### Example 2: Get a webPart object using select

#### Request

With `$select` statement, you can retrieve selected webpart metadata in a request.

```http
GET https://graph.microsoft.com/v1.0/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage/webParts/58ce69a6-bcb0-4f35-b6cd-d757d95f1a8e?$select=id
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.textWebPart",
    "id": "1212fc8d-dd6b-408a-8d5d-9f1cc787efbb"
  }
}
```
