<!-- Source: https://learn.microsoft.com/en-us/graph/api/planview-post-categories?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Create categoryDefinition

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new categoryDefinition object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /planView/categories
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [categoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta) object.

You can specify the following properties when creating a **categoryDefinition**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the category. Required. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [categoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/planView/categories
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.categoryDefinition",
  "displayName": "Marketing",
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.categoryDefinition",
  "id": "6b52004e-a959-a35e-0bc4-3421d8033b1d",
  "displayName": "String",
  "capabilities": {
    "@odata.type": "microsoft.graph.categoryDefinitionCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
