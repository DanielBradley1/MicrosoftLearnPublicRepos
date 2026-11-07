<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-post-distributionlists?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# Create distributionList

Namespace: microsoft.graph

Create a new [personal distribution list](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) in the user's mailbox.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Contacts.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Contacts.ReadWrite | Not available. |
| Application | Contacts.ReadWrite | Not available. |

## HTTP request

```http
POST /me/distributionLists
POST /users/{id | userPrincipalName}/distributionLists
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) object.

You can specify the following properties when you create a **distributionList**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the distribution list. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/me/distributionLists
Content-Type: application/json

{
  "displayName": "Project Team"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user-id')/distributionLists/$entity",
  "id": "AAMkAGI2THVSAAA=",
  "changeKey": "CQAAABYAAABE",
  "createdDateTime": "2024-03-15T10:30:00Z",
  "lastModifiedDateTime": "2024-03-15T10:30:00Z",
  "categories": [],
  "displayName": "Project Team",
  "personId": "e527d18c-9c02-4af4-b5da-729744507c9b"
}
```
