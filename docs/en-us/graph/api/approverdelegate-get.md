<!-- Source: https://learn.microsoft.com/en-us/graph/api/approverdelegate-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# Get approverDelegate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties of the [approverDelegate](https://learn.microsoft.com/en-us/graph/api/resources/approverdelegate?view=graph-rest-beta) object that is configured for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta). The approver delegate identifies the user or group that can approve or deny Microsoft Entra entitlement management access package assignment requests and access reviews on behalf of the user, and the period during which the delegation is in effect.

Signed-in users can read their own approver delegate. Administrators can read the approver delegate of any user in the tenant.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.Read.All | EntitlementManagement.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Identity Governance Administrator

No directory role is required to read your own approver delegate through the `/me` path.

## HTTP request

To read the approver delegate of the signed-in user:

```http
GET /me/identityGovernance/approverDelegate
```

To read the approver delegate of another user:

```http
GET /users/{user-id}/identityGovernance/approverDelegate
```

## Optional query parameters

This method doesn't support any [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [approverDelegate](https://learn.microsoft.com/en-us/graph/api/resources/approverdelegate?view=graph-rest-beta) object in the response body.

If no approver delegate is configured for the user, this method returns a `200 OK` response code and `null` in the response body.

## Examples

### Example 1: Get the approver delegate of the signed-in user

#### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/beta/me/identityGovernance/approverDelegate
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('87ec4b08-df41-4e9c-8f0c-2e6c9e19b0d3')/identityGovernance/approverDelegate",
  "delegate": {
    "@odata.type": "#microsoft.graph.singleUser",
    "id": "d8f4bcd2-4d5a-4a1e-88a5-b0f1c98d2f27",
    "description": "Alex Wilber"
  },
  "schedule": {
    "startDateTime": "2026-08-31T08:21:41.338Z",
    "expiration": {
      "endDateTime": "2026-09-07T08:21:41.339Z",
      "type": "afterDateTime"
    }
  }
}
```

### Example 2: Get the approver delegate of another user

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/users/87ec4b08-df41-4e9c-8f0c-2e6c9e19b0d3/identityGovernance/approverDelegate
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('87ec4b08-df41-4e9c-8f0c-2e6c9e19b0d3')/identityGovernance/approverDelegate",
  "delegate": {
    "@odata.type": "#microsoft.graph.groupMembers",
    "id": "1c5f0b3e-8d4a-4e39-9f2b-6a7c1d3e5f80",
    "description": "Contoso approvers"
  },
  "schedule": {
    "startDateTime": "2026-08-31T08:21:41.338Z",
    "expiration": {
      "type": "noExpiration"
    }
  }
}
```
