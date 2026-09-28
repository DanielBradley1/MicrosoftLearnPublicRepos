<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-restore-recyclebinitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-22 -->

# recycleBinItem: restore

Namespace: microsoft.graph

Restore [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) objects from the [recycleBin](https://learn.microsoft.com/en-us/graph/api/resources/recyclebin?view=graph-rest-1.0) of a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Selected | Not available. |
| Delegated \(personal Microsoft account\) | FileStorageContainer.Selected | Not available. |
| Application | FileStorageContainer.Selected | Not available. |

In addition to Microsoft Graph permissions, your app also must have the necessary container-type level permission or permissions to call this API. For details about container types, see [Container Types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container-type level permissions, see [SharePoint Embedded Authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#Authorization).

## HTTP request

```http
POST /storage/fileStorage/containers/{containerId}/recycleBin/items/restore
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) objects to restore.

## Response

If successful, this method returns a `207 Multi-Status` response code and the set of restored [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/recycleBin/items/restore
Content-Type: application/json

{
  "ids": ["5d625d33-338c-4a77-a98a-3e287116440c", "73133853-48f2-4956-bc4a-03f8d1675042"]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const recycleBinItem = {
  ids: ['5d625d33-338c-4a77-a98a-3e287116440c', '73133853-48f2-4956-bc4a-03f8d1675042']
};

await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/recycleBin/items/restore')
	.post(recycleBinItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 207 Multi-Status
Content-Type: application/json

{
  "value": [
    {
      "id": "5d625d33-338c-4a77-a98a-3e287116440c"
    },
    {
      "id": "73133853-48f2-4956-bc4a-03f8d1675042"
    }
  ]
}
```
