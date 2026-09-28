<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedule-delete-daynotes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# Delete dayNote

Namespace: microsoft.graph

Delete a [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

## HTTP request

```http
DELETE /teams/{teamsId}/schedule/dayNotes/{dayNoteId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
DELETE /teams/d72f9b8e-4c76-4f50-bf93-51b17aab0cd9/schedule/dayNotes/NOTE_ff2194ab-0ae5-43e3-acb4-ec2654927213
```

### Response

```http
HTTP/1.1 204 No Content
```
