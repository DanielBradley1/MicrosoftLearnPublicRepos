<!-- Source: https://learn.microsoft.com/en-us/graph/api/planneruser-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Get plannerUser

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of [plannerUser](https://learn.microsoft.com/en-us/graph/api/resources/planneruser?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.Read | Tasks.ReadWrite, Group.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Tasks.Read.All | Tasks.ReadWrite.All |

## HTTP request

```http
GET /me/planner
GET /users/{usersId}/planner
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

If successful, this method returns a `200 OK` response code and a [plannerUser](https://learn.microsoft.com/en-us/graph/api/resources/planneruser?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/me/planner
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.plannerUser",
    "id": "e209ee8b-d448-4b3c-2994-f7ddf819e121",
    "favoritePlanReferences": {
      "@odata.type": "microsoft.graph.plannerFavoritePlanReferenceCollection"
    },
    "recentPlanReferences": {
      "@odata.type": "microsoft.graph.plannerRecentPlanReferenceCollection"
    }
  }
}
```
