<!-- Source: https://learn.microsoft.com/en-us/graph/api/webpart-getposition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# webPart: getPosition

Namespace: microsoft.graph

Get the [webPartPosition](https://learn.microsoft.com/en-us/graph/api/resources/webpartposition?view=graph-rest-1.0) information of a [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Read.All | Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Read.All | Sites.ReadWrite.All |

## HTTP request

```http
GET /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/webParts/{webpart-id}/getPositionOfWebPart
GET /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/canvasLayout/verticalSection/webparts/{webpart-index}/getPositionOfWebPart
GET /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/canvasLayout/horizontalSections/{horizontal-section-id}/columns/{horizontal-section-column-id}/webparts/{webpart-index}/getPositionOfWebPart
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

If successful, this method returns a `200 OK` response code and a [webPartPosition](https://learn.microsoft.com/en-us/graph/api/resources/webpartposition?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following is an example of a request.

```http
GET https://graph.microsoft.com/v1.0/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage/webParts/a3c93a28-806d-4f1a-b4fc-404848b935f6/getPositionOfWebPart
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "columnId": 1.0,
  "horizontalSectionId": 1.0,
  "isInVerticalSection": false,
  "webpartIndex": 1.0
}
```
