<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-onedriveforbusinessrestoresessions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# Create oneDriveForBusinessRestoreSession

Namespace: microsoft.graph

Create a new [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) object. To create a granular restore session, granular drive restore artifacts must be present in the payload. A request can't include both [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) and [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) in the same **create** or **update** request.

If no payload is provided when you create the restore session, the request creates an empty `standard` restore session by default.

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
POST /solutions/backupRestore/oneDriveForBusinessRestoreSessions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) object.

You can specify the following properties when you create a **oneDriveForBusinessRestoreSession**.

| Property | Type | Description |
| :--- | :--- | :--- |
| driveRestoreArtifacts | [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) collection | A collection of [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) objects. Required. |
| granularDriveRestoreArtifacts | [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) collection | A collection of [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) objects. Required. |
| policyId | String | The identifier of the protection policy that scopes the restore session. The service validates that the referenced protection units belong to this policy. Optional. Inherited from [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0). |

## Response

If successful, this method returns a `201 Created` response code and a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Create a standard restore session

The following example shows how to create a standard restore session.

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions
Content-Type: application/json

{
  "policyId": "99999999-aaaa-bbbb-cccc-dddddddddddd",
  "driveRestoreArtifacts": [
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279" },
      "destinationType": "new"
    },
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888280" },
      "destinationType": "new"
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
  "@odata.context": "/solutions/backupRestore/$metadata#oneDriveForBusinessRestoreSession/$entity",
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
      "displayName": "User1"
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
      "displayName": "User2"
    }
  },
  "lastModifiedDateTime": "2023-03-30T12:01:03.45Z"
}
```

### Example 2: Create a granular restore session

The following example shows how to create a granular restore session.

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions
Content-Type: application/json

{
  "granularDriveRestoreArtifacts": [
    {
      "browseSessionId": "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
      "id": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
    },
    {
      "browseSessionId": "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
      "id": "b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
    }
  ]
}
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#oneDriveForBusinessRestoreSession/$entity",
  "id": "959ba739-70b5-43c4-8c90-b2c22014f18b",
  "status": "draft",
  "restoreJobType": "granular",
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
      "displayName": "User1"
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
      "displayName": "User2"
    }
  },
  "lastModifiedDateTime": "2023-03-30T12:01:03.45Z"
}
```
