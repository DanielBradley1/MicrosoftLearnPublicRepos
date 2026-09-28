<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Get agentIdentityBlueprint

Namespace: microsoft.graph

Read the properties and relationships of [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprint.Read.All | Application.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprint.Read.All | Application.Read.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

```http
GET /applications/{id}/microsoft.graph.agentIdentityBlueprint
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/applications/{id}/microsoft.graph.agentIdentityBlueprint
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let agentIdentityBlueprint = await client.api('/applications/{id}/microsoft.graph.agentIdentityBlueprint')
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
  "@odata.type": "#microsoft.graph.agentIdentityBlueprint",
  "id": "08be1f79-37a1-49c0-b444-3075e74d1e8c",
  "appId": "00001111-aaaa-2222-bbbb-3333cccc4444",
  "identifierUris": [
      "api://00001111-aaaa-2222-bbbb-3333cccc4444"
  ],
  "createdByAppId": "14d82eec-204b-4c2f-b7e8-296a70dab67e",
  "createdDateTime": "2025-09-10T17:04:20Z",
  "description": null,
  "disabledByMicrosoftStatus": null,
  "displayName": "My Agent Blueprint",
  "groupMembershipClaims": null,
  "publisherDomain": "contoso.onmicrosoft.com",
  "signInAudience": "AzureADMyOrg",
  "tags": [],
  "tokenEncryptionKeyId": null,
  "uniqueName": null,
  "serviceManagementReference": null,
  "optionalClaims": null,
  "api": {
      "requestedAccessTokenVersion": 2,
      "acceptMappedClaims": null,
      "knownClientApplications": [],
      "oauth2PermissionScopes": [],
      "preAuthorizedApplications": [],
      "tokenEncryptionSetting": {
          "scheme": null,
          "audience": null,
          "automatedTokenVersion": {
              "current": null,
              "available": []
          }
      }
  },
  "appRoles": [],
  "info": {
      "termsOfServiceUrl": null,
      "supportUrl": null,
      "privacyStatementUrl": null,
      "marketingUrl": null,
      "logoUrl": null
  },
  "keyCredentials": [],
  "passwordCredentials": [],
  "requiredResourceAccess": [],
  "verifiedPublisher": {
      "displayName": null,
      "verifiedPublisherId": null,
      "addedDateTime": null
  },
  "web": {
      "redirectUris": [],
      "homePageUrl": null,
      "logoutUrl": null,
      "redirectUriSettings": [],
      "implicitGrantSettings": {
          "enableIdTokenIssuance": false,
          "enableAccessTokenIssuance": false
      }
  }
}
```
