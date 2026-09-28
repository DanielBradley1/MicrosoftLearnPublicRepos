<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-lock?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-26 -->

# fileStorageContainer: lock

Namespace: microsoft.graph

Lock a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) to prevent modifications to its contents.

This action updates the [lockState](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#sitelockstate-values).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Selected | FileStorageContainer.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | FileStorageContainer.Selected | Not available. |

In addition to Microsoft Graph permissions, your app also must have the necessary container-type level permission or permissions to call this API. For details about container types, see [Container Types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container-type level permissions, see [SharePoint Embedded Authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#Authorization).

Note

When delegated permissions are used, only members who are assigned the `owner` role can call this method.

## HTTP request

```http
POST /storage/fileStorage/containers/{containerId}/lock
```

## Request body

In the request body, you can optionally include a JSON representation of the **lockState** property.

```json
{
    "lockState": "lockedReadOnly"
}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows how to lock a fileStorageContainer.

```http
POST https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/lock

{
    "lockState": "lockedReadOnly"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
