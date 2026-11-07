<!-- Source: https://learn.microsoft.com/en-us/graph/api/distributionlist-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# Update distributionList

Namespace: microsoft.graph

Update the properties of a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Contacts.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Contacts.ReadWrite | Not available. |
| Application | Contacts.ReadWrite | Not available. |

## HTTP request

```http
PATCH /me/distributionLists/{distributionList-id}
PATCH /users/{id | userPrincipalName}/distributionLists/{distributionList-id}
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
| displayName | String | The display name of the distribution list. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/me/distributionLists/AAMkAGI2THVSAAA=
Content-Type: application/json

{
  "displayName": "Updated Project Team"
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
  "changeKey": "CQAAABYAAABG",
  "createdDateTime": "2024-03-15T10:30:00Z",
  "lastModifiedDateTime": "2024-03-25T09:45:00Z",
  "categories": [],
  "displayName": "Updated Project Team",
  "personId": "e527d18c-9c02-4af4-b5da-729744507c9b"
}
```
