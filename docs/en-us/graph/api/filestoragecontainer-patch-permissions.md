<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-patch-permissions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# Upsert permissions

Namespace: microsoft.graph

Upsert \(create or update\) up to 40 [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) objects on a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) in a single request. Delta patch allows the caller to perform multiple operations \(create, update\) on multiple permissions with a single request.

Important

Permissions added to a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) apply to all its [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) objects, regardless of any unique or restrictive permissions applied to those items.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Selected | FileStorageContainer.Manage.All |
| Delegated \(personal Microsoft account\) | FileStorageContainer.Selected | Not available. |
| Application | FileStorageContainer.Selected | Not available. |

In addition to Microsoft Graph permissions, your app also must have the necessary container-type level permission or permissions to call this API. For details about container types, see [Container Types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container-type level permissions, see [SharePoint Embedded Authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#Authorization).

## HTTP request

```HTTP
PATCH /storage/fileStorage/containers/{containerId}/permissions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON object with the following properties.

| Name | Type | Description |
| :--- | :--- | :--- |
| @context | String | OData annotation that identifies the payload type. Must be set to `#$delta` to signal a delta patch operation. Required. |
| value | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) collection | A collection of up to 40 **permission** objects to process. Required. |

Each entry in the **value** collection represents one operation on a [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0). The presence of the **id** property determines how the entry is interpreted. Include the ID of an existing permission to update it, or omit the ID to create a new permission.

Each entry supports the following properties and annotations:

| Name | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the existing permission. When the ID is present, the item is treated as an update. When the ID is omitted, the item is treated as a create operation. Optional. |
| grantedToV2 | [sharePointIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentityset?view=graph-rest-1.0) | For user-type permissions, specify the details of the user for this permission. Required for create operations. Don't specify for update operations. |
| roles | String collection | The type of permission to grant. The possible values are: `reader`, `writer`, `manager`, `owner`. Required for both create and update operations. |
| @microsoft.graph.conflictBehavior | String | An annotation parameter that controls behavior when the target identity is already a member of the container with a different role. Possible values are: `fail`, `replace`. The default value is `fail`. Applies only to create operations. Optional. |

The **@microsoft.graph.conflictBehavior** annotation is per item. The default value `fail` causes the item to fail with a per-item `409 Conflict` response code. The value `replace` replaces the existing role for the identity with the role specified in the item, and the item succeeds. Any other value causes the item to fail with a per-item `400 Bad Request` response code.

Update items must not include properties other than ID and roles. The **roles** property is required. Items that violate either rule fail with a per-item `400 Bad Request` response code.

## Response

If successful, this method returns a `200 OK` response code and a collection of [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) objects in the response body. Permissions that are processed successfully include a **permission** object. Failed items include a **@Core.DataModificationException** annotation with error details.

This API might also return the following error response codes for the entire request:

| HTTP code | Description |
| :--- | :--- |
| 400 | Bad request. |
| 401 | Request lacks valid authentication credentials. |
| 403 | Provided authentication credentials are valid but insufficient to perform requested operation. Example scenarios: The calling app doesn't have permission to manage permissions for containers of this type, or the calling user has no permissions on this container instance, or their role doesn't allow container permission management. |
| 404 | Container doesn't exist. |
| 423 | Container is locked. For example, the container is archived. |

## Examples

### Request

The following example shows a single delta patch request that mixes create and update items in one call. Items without an ID are treated as create operations; items with an ID are treated as update operations. Items that fail are reported inline with a **@Core.DataModificationException** annotation. The remaining items still succeed.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/permissions
Content-Type: application/json

{
  "@context": "#$delta",
  "value": [
    {
      "roles": ["reader"],
      "grantedToV2": {
        "user": {
          "userPrincipalName": "alex@contoso.com"
        }
      }
    },
    {
      "@microsoft.graph.conflictBehavior": "replace",
      "roles": ["writer"],
      "grantedToV2": {
        "user": {
          "userPrincipalName": "kate@contoso.com"
        }
      }
    },
    {
      "roles": ["owner"],
      "grantedToV2": {
        "user": {
          "userPrincipalName": "mike@contoso.com"
        }
      }
    },
    {
      "id": "X2k6MCMuZnxtZW1iZXJzaGlwfGFsZXhAY29udG9zby5jb20",
      "roles": ["manager"]
    },
    {
      "id": "X2k6MCMuZnxtZW1iZXJzaGlwfG5vdGFmb3VuZEBjb250b3NvLmNvbQ",
      "roles": ["manager"]
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permissions = {
  '@context': '#$delta',
  value: [
    {
      roles: ['reader'],
      grantedToV2: {
        user: {
          userPrincipalName: 'alex@contoso.com'
        }
      }
    },
    {
      '@microsoft.graph.conflictBehavior': 'replace',
      roles: ['writer'],
      grantedToV2: {
        user: {
          userPrincipalName: 'kate@contoso.com'
        }
      }
    },
    {
      roles: ['owner'],
      grantedToV2: {
        user: {
          userPrincipalName: 'mike@contoso.com'
        }
      }
    },
    {
      id: 'X2k6MCMuZnxtZW1iZXJzaGlwfGFsZXhAY29udG9zby5jb20',
      roles: ['manager']
    },
    {
      id: 'X2k6MCMuZnxtZW1iZXJzaGlwfG5vdGFmb3VuZEBjb250b3NvLmNvbQ',
      roles: ['manager']
    }
  ]
};

await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/permissions')
	.update(permissions);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response. The first two create items succeed \(the second item replaces the existing role for the target user\). The third create item fails because the identity is already a member of the container with a different role. The first update item succeeds; the second fails because no permission with that id exists.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#storage/fileStorage/containers('b%21ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z')/permissions/$delta",
  "value": [
    {
      "id": "X2k6MCMuZnxtZW1iZXJzaGlwfGFsZXhAY29udG9zby5jb20",
      "roles": [
        "reader"
      ],
      "grantedToV2": {
        "user": {
          "displayName": "Alex Wilson",
          "id": "1a2b3c4d-1111-2222-3333-444455556666",
          "userPrincipalName": "alex@contoso.com"
        }
      }
    },
    {
      "id": "X2k6MCMuZnxtZW1iZXJzaGlwfGthdGVAY29udG9zby5jb20",
      "roles": [
        "writer"
      ],
      "grantedToV2": {
        "user": {
          "displayName": "Kate Brown",
          "id": "2b3c4d5e-2222-3333-4444-555566667777",
          "userPrincipalName": "kate@contoso.com"
        }
      }
    },
    {
      "@Core.DataModificationException": {
        "@odata.type": "#Org.OData.Core.V1.DataModificationExceptionType",
        "failedOperation": "Create",
        "responseCode": 409,
        "info": {
          "code": "Conflict",
          "message": "Conflict: this identity is a [Reader] member of the container and cannot be added to the [Owner] role."
        }
      },
      "id": "00000000-0000-0000-0000-000000000000",
      "roles": [
        "owner"
      ],
      "grantedToV2": {
        "user": {
          "userPrincipalName": "mike@contoso.com"
        }
      }
    },
    {
      "id": "X2k6MCMuZnxtZW1iZXJzaGlwfGFsZXhAY29udG9zby5jb20",
      "roles": [
        "manager"
      ],
      "grantedToV2": {
        "user": {
          "displayName": "Alex Wilson",
          "id": "1a2b3c4d-1111-2222-3333-444455556666",
          "userPrincipalName": "alex@contoso.com"
        }
      }
    },
    {
      "@Core.DataModificationException": {
        "@odata.type": "#Org.OData.Core.V1.DataModificationExceptionType",
        "failedOperation": "Update",
        "responseCode": 404,
        "info": {
          "code": "NotFound",
          "message": "Item not found."
        }
      },
      "id": "X2k6MCMuZnxtZW1iZXJzaGlwfG5vdGFmb3VuZEBjb250b3NvLmNvbQ"
    }
  ]
}
```
