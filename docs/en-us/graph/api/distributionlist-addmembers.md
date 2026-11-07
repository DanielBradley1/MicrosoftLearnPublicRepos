<!-- Source: https://learn.microsoft.com/en-us/graph/api/distributionlist-addmembers?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# distributionList: addMembers

Namespace: microsoft.graph

Add members to a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Contacts.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Contacts.ReadWrite | Not available. |
| Application | Contacts.ReadWrite | Not available. |

## HTTP request

```http
POST /me/distributionLists/{distributionList-id}/addMembers
POST /users/{id | userPrincipalName}/distributionLists/{distributionList-id}/addMembers
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| members | [member](https://learn.microsoft.com/en-us/graph/api/resources/member?view=graph-rest-1.0) collection | The members to add to the distribution list. Each member must include **type** and either **key**, **memberId**, or both. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/me/distributionLists/AAMkAGI2THVSAAA=/addMembers
Content-Type: application/json

{
  "members": [
    {
      "displayName": "Megan Bowen",
      "key": "MeganB@contoso.com",
      "type": "mailbox"
    }
  ]
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user-id')/distributionLists/$entity",
  "id": "AAMkAGI2THVSAAA=",
  "displayName": "Project Team",
  "lastModifiedDateTime": "2024-03-17T11:00:00Z"
}
```
