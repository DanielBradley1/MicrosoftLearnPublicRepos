<!-- Source: https://learn.microsoft.com/en-us/graph/api/restoresessionbase-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# Get restoreSessionBase

Namespace: microsoft.graph

Get the properties of a [restoreSession](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0) object by ID.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.Read.All | Not available. |

## HTTP request

```http
GET /solutions/backupRestore/restoreSessions/{restoreSessionBaseId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/restoreSessions/959ba739-70b5-43c4-8c90-b2c22014f18b
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.sharepointRestoreSession",
  "id": "959ba739-70b5-43c4-8c90-b2c22014f18b",
  "status": "active",
  "restoreJobType": "standard",
  "policyId": "99999999-aaaa-bbbb-cccc-dddddddddddd",
  "restoreSessionArtifactCount": {
    "total": 2,
    "completed": 1,
    "inProgress": 1,
    "failed": 0
  },
  "createdBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "Ryan"
    }
  },
  "createdDateTime": "2023-03-30T12:01:03.45Z",
  "lastModifiedBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "Ryan"
    }
  },
  "lastModifiedDateTime": "2023-03-30T12:01:03.45Z"
}
```
