<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicylink-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Update webFilteringPolicyLink

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update a [webFilteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicylink?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
PATCH /networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}
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
| state | [microsoft.graph.networkaccess.status](https://learn.microsoft.com/en-us/graph/api/resources/enums-networkaccess?view=graph-rest-beta#status-values) | The state of the policy link. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| version | String | The version of the object. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.networkaccess.webFilteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicylink?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/networkAccess/filteringProfiles/d734d2de-f2df-4b4a-8c4c-5111f8878275/policies/70405a6c-b823-4521-8981-de9d08a21f8f
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringPolicyLink",
  "state": "enabled",
  "version": "1.0"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringPolicyLink",
  "id": "e7c17cf0-2140-4b2a-9ec4-564c03709f8e",
  "state": "enabled",
  "version": "1.0"
}
```
