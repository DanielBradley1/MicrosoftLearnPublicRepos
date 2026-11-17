<!-- Source: https://learn.microsoft.com/en-us/graph/api/categorydefinition-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# List categories

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) with its [category definitions](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta) expanded through **planView**. Categories belong to a plan; `/planView/categories` isn't a standalone root collection. To locate one category, find its ID in the returned **planView.categories** array.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.Read | Tasks.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Tasks.Read.All | Tasks.ReadWrite.All |

## HTTP request

```http
GET /planner/plans_v2/{planId}?$expand=planView($expand=categories)
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) object with **planView.categories** expanded in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/planner/plans_v2/b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31?$expand=planView($expand=categories)
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plan",
  "id": "b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31",
  "displayName": "Product launch",
  "planView": {
    "categories": [
      {
        "id": "6b52004e-a959-a35e-0bc4-3421d8033b1d",
        "displayName": "Launch readiness"
      }
    ]
  }
}
```
