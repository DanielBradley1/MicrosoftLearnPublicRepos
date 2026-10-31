<!-- Source: https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# Update oneDriveForBusinessRestoreSession

Namespace: microsoft.graph

Update the properties of a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /solutions/backupRestore/oneDriveForBusinessRestoreSessions/{oneDriveForBusinessRestoreSessionId}
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
| driveRestoreArtifacts | [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) collection | Collection of [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0). Required |
| granularDriveRestoreArtifacts | [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) collection | A collection of [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) objects. Required. |
| policyId | String | The identifier of the protection policy that scopes the restore session. When supplied, the service validates that referenced protection units belong to this policy. Inherited from [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0). |

To remove a **driveRestoreArtifact** from a standard restore session, specify the `@removed` annotation in the request body together with the ID of the [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) object.

To remove a **granularDriveRestoreArtifact** from a granular restore session, specify the `@removed` annotation in the request body for the respective artifact ID of the [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0).

## Response

If successful, this method returns a `200 OK` response code and an updated [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Update a standard restore session

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions/1b014d8c-71fe-4d00-8ab2-31850bc5b32c

{
  "policyId": "99999999-aaaa-bbbb-cccc-dddddddddddd",
  "driveRestoreArtifacts@delta": [
    {
      "restorePoint": { "id": "1b014d8c-71fe-4d00-a01a-31850bc5b32c" }, //Create a new drive restore artifact and add it under the Restore Session.
      "destinationType": "new"
    },
    {
      "restorePoint": { "id": "2b014d8c-71fe-4d00-a01a-31850bc5b32" },
      "destinationType": "new"
    },
    {
      "restorePoint": { "id": "3b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new"
    },
    {
      "restorePoint": { "id": "4b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "99954f18-c8ec-4b62-85bf-cdf3b70b140e"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "4267e382-71a9-4c07-bef7-bda97e09c0d2"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "3667e382-71a9-4c07-bef7-bda97e09c0d2"
    }
  ]
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK

{
  "driveRestoreArtifacts@delta": [
    {
      "id": "89014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "1b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "67014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "2b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "56014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "3b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "32014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "4b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      //Error scenario
      "@contentId": "3467e382-71a9-4c07-bef7-bda97e09c0d2", // To add context and more traceability.
      "@Core.DataModificationException": {
        "info": {
          "code": "Invalid",
          "message": "The identifier to be removed from the restore session does not exist"
        },
        "failedOperation": "remove",
        "responseCode": 409
      },
      "id": "4267e382-71a9-4c07-bef7-bda97e09c0d2"
    }
  ]
}
```

### Example 2: Update a granular restore session

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions/43e0638e-3ad7-4c7e-8749-72175d046e30
Content-Type: application/json

{
  "granularDriveRestoreArtifacts@delta": [
    {
      "browseSessionId": "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE",
      "itemKey": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
    }
  ]
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@context": "#$delta",
  "id": "43e0638e-3ad7-4c7e-8749-72175d046e30",
  "granularDriveRestoreArtifacts@delta": [
    {
      "directoryObjectId": null,
      "id": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
      "browseSessionId": "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE",
      "restoredItemKey": "",
      "webUrl": "",
      "restoredItemPath": null,
      "restoredItemWebUrl": "",
      "status": "added",
      "restorePointDateTime": "0001-01-01T00:00:00Z",
      "startDateTime": "0001-01-01T00:00:00Z",
      "completionDateTime": "0001-01-01T00:00:00Z"
    },
    {
      "id": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
      "@removed": {
        "reason": "changed"
      }
    }
  ]
}
```
