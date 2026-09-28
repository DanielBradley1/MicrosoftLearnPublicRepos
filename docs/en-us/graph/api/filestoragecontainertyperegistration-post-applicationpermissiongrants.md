<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainertyperegistration-post-applicationpermissiongrants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create fileStorageContainerTypeAppPermissionGrant

Namespace: microsoft.graph

Create a new [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) object in a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainerTypeReg.Selected | FileStorageContainerTypeReg.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | FileStorageContainerTypeReg.Selected | Not available. |

Note

- When delegated tokens are used, either the SharePoint Embedded admin role or the Global admin role is required.
- If the `FileStorageContainerTypeReg.Selected` permission is used, changes are limited to [registrations](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) owned by the application that makes the call.
- Created permission grants may take up to one hour to propagate.

## HTTP request

```http
PUT /storage/fileStorage/containerTypeRegistrations/{fileStorageContainerTypeRegistrationId}/applicationPermissionGrants/{appId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) object. Don't include the **appId** in the body.

You can specify the following properties when you create a **fileStorageContainerTypeAppPermissionGrant**.

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationPermissions | fileStorageContainerTypeAppPermission collection | Allowed [permissions](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/auth#grant-container-type-application-permissions) when you use application tokens. The possible values are: `none`, `readContent`, `writeContent`, `manageContent`, `create`, `delete`, `read`, `write`, `enumeratePermissions`, `addPermissions`, `updatePermissions`, `deletePermissions`, `deleteOwnPermission`, `managePermissions`, `full`, `unknownFutureValue`. Optional. |
| delegatedPermissions | fileStorageContainerTypeAppPermission collection | Allowed [permissions](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/auth#grant-container-type-application-permissions) when you use delegated tokens. The possible values are: `none`, `readContent`, `writeContent`, `manageContent`, `create`, `delete`, `read`, `write`, `enumeratePermissions`, `addPermissions`, `updatePermissions`, `deletePermissions`, `deleteOwnPermission`, `managePermissions`, `full`, `unknownFutureValue`. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows how to add a new permission grant to a registration.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypeRegistrations/33225700-9a00-4c00-84dd-0c210f203f01/applicationPermissionGrants/11335700-9a00-4c00-84dd-0c210f203f00
Content-Type: application/json

{
  "delegatedPermissions": ["readContent", "writeContent"],
  "applicationPermissions": ["full"]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerTypeAppPermissionGrant = {
  delegatedPermissions: ['readContent', 'writeContent'],
  applicationPermissions: ['full']
};

await client.api('/storage/fileStorage/containerTypeRegistrations/33225700-9a00-4c00-84dd-0c210f203f01/applicationPermissionGrants/11335700-9a00-4c00-84dd-0c210f203f00')
	.put(fileStorageContainerTypeAppPermissionGrant);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fileStorageContainerTypeAppPermissionGrant",
  "appId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "delegatedPermissions": ["readContent", "writeContent"],
  "applicationPermissions": ["full"]
}
```
