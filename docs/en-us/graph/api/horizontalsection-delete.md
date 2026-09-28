<!-- Source: https://learn.microsoft.com/en-us/graph/api/horizontalsection-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Delete horizontalSection

Namespace: microsoft.graph

Remove a [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) from a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

> **Note:** To delete an item, the user must have granted the application write access to the item to be deleted.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Not available. |

## HTTP request

```http
DELETE /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/canvasLayout/horizontalSections/{horizontal-section-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. |

## Request body

Don't supply a request body with this method.

## Response

If successful, this call returns a `204 No Content` response to indicate that the resource was deleted and there was nothing to return.

If the target horizontal section is not found, this method returns `404 Not Found`.

## Example

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage/canvasLayout/horizontalSections/1
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
