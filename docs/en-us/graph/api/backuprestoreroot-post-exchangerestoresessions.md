<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-exchangerestoresessions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# Create exchangeRestoreSession

Namespace: microsoft.graph

Create a new [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.ReadWrite.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/exchangeRestoreSessions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0).

You can specify the following properties when you create an **exchangeRestoreSession** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| granularMailboxRestoreArtifact | [granularMailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularmailboxrestoreartifact?view=graph-rest-1.0) collection | Collection of [granularMailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularmailboxrestoreartifact?view=graph-rest-1.0) objects. |
| mailboxRestoreArtifacts | [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) collection | Collection of [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) objects. |
| policyId | String | The identifier of the protection policy that scopes the restore session. The service validates that the referenced protection units belong to this policy. Optional. Inherited from [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0). |

## Response

If successful, this method returns a `201 Created` response code and an [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Create exchangeRestoreSession with mailboxRestoreArtifacts

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeRestoreSessions
Content-Type: application/json

{
  "policyId": "99999999-aaaa-bbbb-cccc-dddddddddddd",
  "mailboxRestoreArtifacts": [
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279" },
      "destinationType": "inPlace"
    },
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888280" },
      "destinationType": "inPlace"
    }
  ]
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#exchangeRestoreSessions/$entity",
  "id": "959ba739-70b5-43c4-8c90-b2c22014f18b",
  "status": "draft",
  "restoreJobType": "standard",
  "policyId": "99999999-aaaa-bbbb-cccc-dddddddddddd",
  "restoreSessionArtifactCount": {
    "total": 2,
    "completed": 0,
    "inProgress": 0,
    "failed": 0
  },
  "createdBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "ABC"
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
      "displayName": "DEF"
    }
  },
  "lastModifiedDateTime": "2023-03-30T12:01:03.45Z",
  "error": null
}
```

### Example 2: Create exchangeRestoreSession with granularMailboxRestoreArtifact

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeRestoreSessions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.exchangeRestoreSession",
  "granularMailboxRestoreArtifacts": [
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279" },
      "destinationType": "inPlace",
      "searchResponseId" : "M2UyZDAwMDAwMDMxMzkzYTMyNj"
    }
  ]
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#exchangeRestoreSessions/$entity",
  "id": "959ba739-70b5-43c4-8c90-b2c22014f18b",
  "status": "draft",
  "restoreJobType": "standard",
  "restoreSessionArtifactCount": {
    "total": 2,
    "completed": 0,
    "inProgress": 0,
    "failed": 0
  },
  "createdBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "ABC"
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
      "displayName": "DEF"
    }
  },
  "lastModifiedDateTime": "2023-03-30T12:01:03.45Z",
  "error": null,
  "granularMailboxRestoreArtifact": [
    {
      "id": "959ba739-70b5-43c4-8c90-b2c22014f18a",
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279" },
      "restoredFolderId": null,
      "status": "added",
      "startDateTime": null,
      "destinationType": "inPlace",
      "searchResponseId": "M2UyZDAwMDAwMDMxMzkzYTMyNj",
      "error": null
    }
  ]
}
```
