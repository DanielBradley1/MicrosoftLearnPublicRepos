<!-- Source: https://learn.microsoft.com/en-us/graph/api/plan-list-customfielddefinitions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# List customFieldDefinition objects

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the customFieldDefinition objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /me/planner/plans_v2/{planId}/customFieldDefinitions
GET /users/{usersId}/planner/plans_v2/{planId}/customFieldDefinitions
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

If successful, this method returns a `200 OK` response code and a collection of [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/me/planner/plans_v2/{planId}/customFieldDefinitions
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.customFieldDefinition",
      "id": "590f4e29-112d-432c-491b-21a16ed31803",
      "planId": "String",
      "displayName": "String",
      "valueType": "String",
      "rollupType": "String",
      "createdBy": {
        "@odata.type": "microsoft.graph.identitySet"
      },
      "createdDateTime": "String (timestamp)",
      "lastModifiedBy": {
        "@odata.type": "microsoft.graph.identitySet"
      },
      "lastModifiedDateTime": "String (timestamp)",
      "deletedBy": {
        "@odata.type": "microsoft.graph.identitySet"
      },
      "deletedDateTime": "String (timestamp)",
      "archivalInfo": {
        "@odata.type": "microsoft.graph.plannerArchivalInfo"
      }
    }
  ]
}
```
