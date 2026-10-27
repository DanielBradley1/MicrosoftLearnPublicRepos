<!-- Source: https://learn.microsoft.com/en-us/graph/api/approverdelegate-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# Update approverDelegate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create or replace the [approverDelegate](https://learn.microsoft.com/en-us/graph/api/resources/approverdelegate?view=graph-rest-beta) object that is configured for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta). The approver delegate can approve or deny Microsoft Entra entitlement management access package assignment requests and access reviews on behalf of the user for the period that you specify in the schedule.

The delegation applies to all access package assignment requests and access reviews that are assigned to the user. While the delegation is in effect, the user can still approve or deny their own pending items.

Signed-in users can set their own approver delegate. Administrators can set the approver delegate of any user in the tenant.

Because this method is a `PUT` operation, the request body replaces the existing approver delegate. To stop a delegation, submit a new approver delegate with a schedule that has already expired.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Identity Governance Administrator* is the least privileged role supported for this operation.

No directory role is required to set your own approver delegate through the `/me` path.

## HTTP request

To set the approver delegate of the signed-in user:

```http
PUT /me/identityGovernance/approverDelegate
```

To set the approver delegate of another user:

```http
PUT /users/{user-id}/identityGovernance/approverDelegate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [approverDelegate](https://learn.microsoft.com/en-us/graph/api/resources/approverdelegate?view=graph-rest-beta) object.

The following table shows the properties that you can use when you set an approver delegate.

| Property | Type | Description |
| :--- | :--- | :--- |
| delegate | [userSet](https://learn.microsoft.com/en-us/graph/api/resources/userset?view=graph-rest-beta) | The user or group that receives the approval delegation. Specify the `@odata.type` property to identify the subtype. Only the [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-beta) and [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-beta) subtypes are supported. Required. |
| schedule | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-beta) | The period during which the delegation is in effect. If you don't specify a schedule, the delegation starts immediately and doesn't expire. Optional. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

### Errors

This method returns the following error when the delegate isn't a supported [userSet](https://learn.microsoft.com/en-us/graph/api/resources/userset?view=graph-rest-beta) subtype, or when the delegate can't be resolved.

| HTTP status code | Error code | Error message |
| :--- | :--- | :--- |
| 400 | Request\_BadRequest | Invalid or unsupported approver delegate. |

## Examples

### Example 1: Set a user as the approver delegate of the signed-in user

#### Request

The following example delegates approvals to a single user for one week.

```http
PUT https://graph.microsoft.com/beta/me/identityGovernance/approverDelegate
Content-type: application/json

{
  "delegate": {
    "@odata.type": "#microsoft.graph.singleUser",
    "id": "d8f4bcd2-4d5a-4a1e-88a5-b0f1c98d2f27"
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

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Set a group as the approver delegate of another user

#### Request

The following example delegates approvals for another user to the members of a group, with no expiration.

```http
PUT https://graph.microsoft.com/beta/users/87ec4b08-df41-4e9c-8f0c-2e6c9e19b0d3/identityGovernance/approverDelegate
Content-type: application/json

{
  "delegate": {
    "@odata.type": "#microsoft.graph.groupMembers",
    "id": "1c5f0b3e-8d4a-4e39-9f2b-6a7c1d3e5f80"
  },
  "schedule": {
    "startDateTime": "2026-08-31T08:21:41.338Z",
    "expiration": {
      "type": "noExpiration"
    }
  }
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
