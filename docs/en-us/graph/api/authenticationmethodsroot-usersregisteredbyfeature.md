<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationmethodsroot-usersregisteredbyfeature?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# authenticationMethodsRoot: usersRegisteredByFeature

Namespace: microsoft.graph

Get the number of users capable of multi-factor authentication, self-service password reset, and passwordless authentication.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AuditLog.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Reports Reader
- Security Reader
- Security Administrator
- Global Reader

## HTTP request

```http
GET /reports/authenticationMethods/usersRegisteredByFeature
```

## Function parameters

The following table shows the parameters that can be used with this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| includedUserRoles | includedUserRoles | The role type for the user. The possible values are: `all`, `privilegedAdmin`, `admin`, `user`. |
| includedUserTypes | includedUserTypes | User type. The possible values are: `all`, `member`, `guest`. |

The value `privilegedAdmin` consists of the following [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json):

- Global Administrator
- Security Administrator
- Conditional Access Administrator
- Exchange Administrator
- SharePoint Administrator
- Helpdesk Administrator
- Billing Administrator
- User Administrator
- Authentication Administrator

The value `admin` includes all Microsoft Entra admin roles.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [userRegistrationFeatureSummary](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationfeaturesummary?view=graph-rest-1.0) in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/reports/authenticationMethods/usersRegisteredByFeature(includedUserTypes='all',includedUserRoles='all')
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let userRegistrationFeatureSummary = await client.api('/reports/authenticationMethods/usersRegisteredByFeature(includedUserTypes='all',includedUserRoles='all')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.userRegistrationFeatureSummary",
  "totalUserCount": 23123,
  "userTypes": "all",
  "userRoles": "all",
  "userRegistrationFeatureCounts": [
    {
      "feature": "ssprRegistered",
      "userCount": 23423
    },
    {
      "feature": "ssprEnabled",
      "userCount": 4234
    },
    {
      "feature": "ssprCapable",
      "userCount": 4234
    },
    {
      "feature": "passwordlessCapable",
      "userCount": 323
    },
    {
      "feature": "mfaCapable",
      "userCount": 3345
    }
  ]
}
```
