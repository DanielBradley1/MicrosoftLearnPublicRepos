<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignment-reprocessassignments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# assignment: reprocessAssignments

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Reprocess existing license [assignments](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) for a user by calling the **reprocessAssignments** action on a user's assignments. Depending on the steps taken to resolve licensing errors, it might be necessary to manually trigger the processing of a user to update their state. For example, after you resolve a dependency violation error for an affected user, you need to trigger reprocessing to apply the changes.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudLicensing.AssignLicenses | CloudLicensing.AssignLicenses.Organization, User-CloudLicensing.AssignLicenses, User-CloudLicensing.AssignLicenses.Organization, AgentIdUser.ReadWrite.IdentityParentedBy, AgentIdUser.ReadWrite.All, User.ReadWrite.All, Group-CloudLicensing.AssignLicenses, Group-CloudLicensing.AssignLicenses.Organization, Group.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudLicensing.AssignLicenses.Organization | User-CloudLicensing.AssignLicenses.Organization, AgentIdUser.ReadWrite.IdentityParentedBy, AgentIdUser.ReadWrite.All, User.ReadWrite.All, Group-CloudLicensing.AssignLicenses.Organization, Group.ReadWrite.All, Directory.ReadWrite.All |

## HTTP request

```http
POST /users/{userId}/cloudLicensing/assignments/reprocessAssignments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/users/43fe5b38-7328-40b9-a2f6-85d86ae8c34d/cloudLicensing/assignments/reprocessAssignments
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/users/43fe5b38-7328-40b9-a2f6-85d86ae8c34d/cloudLicensing/assignments/reprocessAssignments')
	.version('beta')
	.post();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
