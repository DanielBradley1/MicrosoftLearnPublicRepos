<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertyperegistrations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create fileStorageContainerTypeRegistration

Namespace: microsoft.graph

Create or replace a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object. This method registers a [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) in the tenant.

For standard containers, [billing](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/administration/billing/billing) must be valid for the registration to complete successfully.

Important

- An application can only register a [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) that it owns, either using app-only or delegated tokens.
- The registration of a container type in a newly created tenant can fail if the tenant isn't yet fully ready. You might need to wait at least an hour before you can register a container type in a new tenant.

Settings can't be modified during registration.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainerTypeReg.Selected | FileStorageContainerTypeReg.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | FileStorageContainerTypeReg.Selected | Not available. |

> **Note:**
> 
> - When delegated tokens are used, either the SharePoint Embedded admin role or the Global admin role is required.
> - The registration must be done in the context of the application that owns the [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0).

## HTTP request

To register a **fileStorageContainerType** in the current tenant.

```http
PUT /storage/fileStorage/containerTypeRegistrations/{fileStorageContainerTypeId}
```

> **Note:** Use the PUT method. This request creates a **fileStorageContainertypeRegistration** object with the provided ID \(**fileStorageContainerTypeId**\).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object.

You can specify the following property when you create a **fileStorageContainerTypeRegistration**.

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationPermissionGrants | [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) collection | The access privileges of applications on containers of a specific **fileStorageContainerType**. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a fileStorageContainerTypeRegistration for a trial fileStorageContainerType

The following example shows how to create a **fileStorageContainerTypeRegistration** for a trial **fileStorageContainerType** with some **applicationPermissionGrants**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypeRegistrations/de988700-d700-020e-0a00-0831f3042f00
Content-Type: application/json

{
  "applicationPermissionGrants": [
    {
      "appId": "11335700-9a00-4c00-84dd-0c210f203f00",
      "delegatedPermissions": ["readContent", "writeContent"],
      "applicationPermissions": ["full"]
    },
    {
      "appId": "d893fd02-3578-4c7f-bd85-12fc3358af48",
      "delegatedPermissions": ["readContent"],
      "applicationPermissions": ["read"]
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerTypeRegistration = {
  applicationPermissionGrants: [
    {
      appId: '11335700-9a00-4c00-84dd-0c210f203f00',
      delegatedPermissions: ['readContent', 'writeContent'],
      applicationPermissions: ['full']
    },
    {
      appId: 'd893fd02-3578-4c7f-bd85-12fc3358af48',
      delegatedPermissions: ['readContent'],
      applicationPermissions: ['read']
    }
  ]
};

await client.api('/storage/fileStorage/containerTypeRegistrations/de988700-d700-020e-0a00-0831f3042f00')
	.put(fileStorageContainerTypeRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fileStorageContainerTypeRegistration",
  "id": "de988700-d700-020e-0a00-0831f3042f00",
  "name": "Test Trial Container",
  "owningAppId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial",
  "billingStatus": "valid",
  "registeredDateTime": "01/20/2025",
  "expirationDateTime": "02/20/2025",
  "etag": "RVRhZw==",
  "settings": {
    "@odata.type": "microsoft.graph.fileStorageContainerTypeRegistrationSettings",
    "sharingCapability": "disabled",
    "urlTemplate": "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
    "isDiscoverabilityEnabled": true,
    "isSearchEnabled": true,
    "isItemVersioningEnabled": true,
    "itemMajorVersionLimit": 50,
    "maxStoragePerContainerInBytes": 104857600,
    "isSharingRestricted": false
  },
  "applicationPermissionGrants": [
    {
      "appId": "11335700-9a00-4c00-84dd-0c210f203f00",
      "delegatedPermissions": ["readContent", "writeContent"],
      "applicationPermissions": ["full"]
    },
    {
      "appId": "d893fd02-3578-4c7f-bd85-12fc3358af48",
      "delegatedPermissions": ["readContent"],
      "applicationPermissions": ["read"]
    }
  ]
}
```

### Example 2: Create a fileStorageContainerTypeRegistration for a standard fileStorageContainerType where billing setup isn't completed

The following example shows how to create a **fileStorageContainerTypeRegistration** for a standard **fileStorageContainerType** where the billing setup isn't completed.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
PUT https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypeRegistrations/52a2630c-5e6a-41ff-8645-15406bafe66a
Content-Type: application/json

{
  "applicationPermissionGrants": [
    {
      "appId": "11335700-9a00-4c00-84dd-0c210f203f00",
      "delegatedPermissions": ["readContent", "writeContent"],
      "applicationPermissions": ["full"]
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerTypeRegistration = {
  applicationPermissionGrants: [
    {
      appId: '11335700-9a00-4c00-84dd-0c210f203f00',
      delegatedPermissions: ['readContent', 'writeContent'],
      applicationPermissions: ['full']
    }
  ]
};

await client.api('/storage/fileStorage/containerTypeRegistrations/52a2630c-5e6a-41ff-8645-15406bafe66a')
	.put(fileStorageContainerTypeRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 405 Method Not Allowed
```
