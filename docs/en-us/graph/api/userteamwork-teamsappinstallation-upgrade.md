<!-- Source: https://learn.microsoft.com/en-us/graph/api/userteamwork-teamsappinstallation-upgrade?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# teamsAppInstallation in personal scope: upgrade

Namespace: microsoft.graph

Upgrade an [app installation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) in the personal scope of the specified [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) to the latest version of the app.

> **Note:** This API works differently in one or more national clouds. For details, see [Microsoft Teams API implementation differences in national clouds](https://learn.microsoft.com/en-us/graph/teamwork-national-cloud-differences).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsAppInstallation.ReadWriteSelfForUser | TeamsAppInstallation.ManageSelectedForUser, TeamsAppInstallation.ReadWriteAndConsentForUser, TeamsAppInstallation.ReadWriteAndConsentSelfForUser, TeamsAppInstallation.ReadWriteForUser, TeamsAppInstallation.ReadWriteSelectedForUser |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsAppInstallation.ReadWriteSelfForUser.All | TeamsAppInstallation.ManageSelectedForUser.All, TeamsAppInstallation.ReadWriteAndConsentForUser.All, TeamsAppInstallation.ReadWriteAndConsentSelfForUser.All, TeamsAppInstallation.ReadWriteForUser.All, TeamsAppInstallation.ReadWriteSelectedForUser.All |

## HTTP request

```http
POST /users/{user-id | user-principal-name}/teamwork/installedApps/{app-installation-id}/upgrade
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of the properties.

The following table shows the properties that can be used with this method.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| consentedPermissionSet | [teamsAppPermissionSet](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0) | Set of resource-specific permissions that are being consented to. Optional. |

> **Note:** The permissions consented to during the install must be the same as the resource-specific permissions present in the [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0) of the app. To get the application and delegated resource-specific permissions, see [List apps installed in the personal scope of a user](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-installedapps?view=graph-rest-1.0). If only delegated resource-specific permissions are present in the **teamsAppDefinition**, then the permissions can be omitted from the request body.

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Examples

### Example 1: Upgrade a specific app installed for a user

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/users/5b649834-7412-4cce-9e69-176e95a394f5/teamwork/installedApps/NWI2NDk4MzQtNzQxMi00Y2NlLTllNjktMTc2ZTk1YTM5NGY1IyNhNmI2MzM2NS0zMWE0LTRmNDMtOTJlYy03MTBiNzE1NTdhZjk/upgrade
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/users/5b649834-7412-4cce-9e69-176e95a394f5/teamwork/installedApps/NWI2NDk4MzQtNzQxMi00Y2NlLTllNjktMTc2ZTk1YTM5NGY1IyNhNmI2MzM2NS0zMWE0LTRmNDMtOTJlYy03MTBiNzE1NTdhZjk/upgrade')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Upgrade a specific app installed for a user and consent to the resource specific permissions

To get the list of resource-specific permissions required by the app, get the app from the **appCatalog**. For details, see [List apps installed in the personal scope of a user](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-installedapps?view=graph-rest-1.0).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/v1.0/users/5b649834-7412-4cce-9e69-176e95a394f5/teamwork/installedApps/NWI2NDk4MzQtNzQxMi00Y2NlLTllNjktMTc2ZTk1YTM5NGY1IyNhNmI2MzM2NS0zMWE0LTRmNDMtOTJlYy03MTBiNzE1NTdhZjk/upgrade
Content-Type: application/json

{
  "consentedPermissionSet": {
    "resourceSpecificPermissions": [
      {
        "permissionValue": "TeamsActivity.Send.User",
        "permissionType": "Application"
      }
    ]
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const upgrade = {
  consentedPermissionSet: {
    resourceSpecificPermissions: [
      {
        permissionValue: 'TeamsActivity.Send.User',
        permissionType: 'Application'
      }
    ]
  }
};

await client.api('/users/5b649834-7412-4cce-9e69-176e95a394f5/teamwork/installedApps/NWI2NDk4MzQtNzQxMi00Y2NlLTllNjktMTc2ZTk1YTM5NGY1IyNhNmI2MzM2NS0zMWE0LTRmNDMtOTJlYy03MTBiNzE1NTdhZjk/upgrade')
	.post(upgrade);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
