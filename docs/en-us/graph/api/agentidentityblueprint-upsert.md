<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-upsert?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Upsert agentIdentityBlueprint

Namespace: microsoft.graph

Create a new [agent identity blueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object if it doesn't exist, or update the properties of an existing object.

Important

Using PATCH to set [**passwordCredential**](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) is not supported. Use the [addPassword](https://learn.microsoft.com/en-us/graph/api/application-addpassword?view=graph-rest-1.0) and [removePassword](https://learn.microsoft.com/en-us/graph/api/application-removepassword?view=graph-rest-1.0) methods to update the password or secret for an agent identity blueprint.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprint.ReadWrite.All | Not available |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprint.ReadWrite.All | Not available |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

To create or update an application, specify the **uniqueName** client-provided alternate key.

```http
PATCH /applications(uniqueName='{uniqueName}')/microsoft.graph.agentIdentityBlueprint
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Prefer | `create-if-missing`. Required for upsert behavior, otherwise the request is treated as an update operation. |

## Request body

In the request body, supply a JSON representation of the [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object. The request body must contain **displayName**, which is a required property. Specify other writable properties as necessary for your agentIdentityBlueprint, for creation or update.

## Response

If an object with **uniqueName** doesn't exist, this method returns a `201 Created` response code and a new agent identity blueprint object in the response body. The agent identity blueprint is assigned the uniqueName value.

If an object with **uniqueName** doesn't exist and the `Prefer: create-if-missing` header is *not* specified, this method returns a `404 Not Found` error code.

If an application object with **uniqueName** already exists, this method updates the object and returns a `204 No Content` response code.

For information about errors returned by agent identity APIs, see [Agent identity error codes](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform/error-codes).

## Examples

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/applications(uniqueName='app-65278')/microsoft.graph.agentIdentityBlueprint
Content-Type: application/json
Prefer: create-if-missing

{
  "displayName": "Display name"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applications/$entity",
    "id": "03ef14b0-ca33-4840-8f4f-d6e91916010e",
    "deletedDateTime": null,
    "appId": "00001111-aaaa-2222-bbbb-3333cccc4444",
    "identifierUris": [],
    "createdDateTime": "2019-09-17T19:10:35.2742618Z",
    "displayName": "Display name",
    "groupMembershipClaims": null,
    "optionalClaims": null,
    "publisherDomain": "contoso.onmicrosoft.com",
    "requiredResourceAccess": [],
    "signInAudience": "AzureADandPersonalMicrosoftAccount",
    "tags": [],
    "tokenEncryptionKeyId": null,
    "api": {
        "requestedAccessTokenVersion": 2,
        "acceptMappedClaims": null,
        "knownClientApplications": [],
        "oauth2PermissionScopes": [],
        "preAuthorizedApplications": []
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
    "uniqueName": "app-65278",
    "web": {
        "redirectUris": [],
        "homePageUrl": null,
        "logoutUrl": null,
        "implicitGrantSettings": {
            "enableIdTokenIssuance": false,
            "enableAccessTokenIssuance": false
        }
    }
}
```
