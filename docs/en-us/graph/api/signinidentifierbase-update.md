<!-- Source: https://learn.microsoft.com/en-us/graph/api/signinidentifierbase-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-04 -->

# Update signInIdentifierBase

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SignInIdentifier.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SignInIdentifier.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Authentication Policy Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /identity/signInIdentifiers/{signInIdentifier-name}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The unique name identifier for this sign-in identifier configuration. Possible values include: `Email`, `UPN`, `Username`, `CustomUsername1`, `CustomUsername2`. Required. |
| isEnabled | Boolean | Indicates whether this sign-in identifier type is enabled for user authentication in the tenant. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/identity/signInIdentifiers/Email
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.signInIdentifierBase",
  "name": "Email",
  "isEnabled": true
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.signInIdentifierBase",
  "name": "Email",
  "isEnabled": true
}
```
