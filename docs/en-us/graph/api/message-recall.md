<!-- Source: https://learn.microsoft.com/en-us/graph/api/message-recall?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-25 -->

# message: recall

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Recall a message in the specified user's mailbox Sent Items folder.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Mail.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Mail.ReadWrite | Not available. |
| Application | Mail.ReadWrite | Not available. |

## HTTP request

```http
POST /me/mailFolders/sentitems/messages/{id}/recall
POST /users/{id | userPrincipalName}/mailFolders/sentitems/messages/{id}/recall
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `202 Accepted` response code and a string that contains server information in the response body.

If the ID is invalid, this method returns a `400 Bad request` and the detailed error information in the response body.

## Example

The following example shows how to call this API.

### Request

The following request recalls the specified message in the specified user's mailbox sent items folder.

> **Note:** The ID here is shortened for readability.

```http
POST https://graph.microsoft.com/beta/me/mailFolders/sentitems/messages/AAMkADhAAATs28OAAA=/recall
```

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
  "Successfully submitted recall request to Hub server LV8PR00MB1800.NAMPRD00.PROD.OUTLOOK.COM, MessageId is CSRUBSZRRANU4.HEXMGAAG0OPH2@dm6pr00mb0830."
}
```
