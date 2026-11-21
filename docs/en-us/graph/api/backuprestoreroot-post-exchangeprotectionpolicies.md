<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-exchangeprotectionpolicies?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Create exchangeProtectionPolicy

Namespace: microsoft.graph

Create a protection policy for the Exchange service in a Microsoft 365 tenant. The policy is set to `inactive` when it is created. Users can also provide a list of protection units under the policy.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Configuration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Configuration.ReadWrite.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/exchangeProtectionPolicies/
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, include a JSON representation of the [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0) object.

You can specify the following properties when you create an **exchangeProtectionPolicy** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the Exchange Protection Policy. |
| mailboxProtectionUnits | [mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0) collection | Collection of the mailboxProtectionUnits to be added to the exchangeProtectionPolicy. |
| retentionSettings | [retentionSetting](https://learn.microsoft.com/en-us/graph/api/resources/retentionsetting?view=graph-rest-1.0) collection | Retention settings for the policy. Optional. If omitted, the default retention period is 365 days. |

## Response

If successful, this method returns a `201 Created` response code and an [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0) object in the response body.

The service returns the complete **retentionSettings** collection, rather than echoing the request collection. The response includes a fixed 14-day period \(`P14D`\) for the `R/PT10M` interval and the configured policy retention period for the `R/P1W` interval. The 14-day period is a service-defined backup tier, not a supported policy retention period for create or update requests.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Request

The following example shows how to create a policy with a retention period of 180 days.

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies
Content-Type: application/json

{
  "displayName": "Exchange Protection Policy",
  "mailboxProtectionUnits": [
    {
      "directoryObjectId": "cdd3a849-dcaf-4a85-af82-7e39fc14019a"
    },
    {
      "directoryObjectId": "9bc069da-b746-41a4-89ab-26125c6373c7"
    },
    {
      "directoryObjectId": "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7"
    }
  ],
  "retentionSettings": [
    {
      "interval": "R/P1W",
      "period": "P180D"
    }
  ]
}
```

### Response

The following example shows the response with the retention settings for both backup intervals, including the requested 180-day retention period.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/ProtectionPolicies/b218eb4a-ea72-42bd-8f0b-d0bbf794bec7

{
  "@odata.context": "/solutions/backupRestore/$metadata#exchangeProtectionPolicies/$entity",
  "id": "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7",
  "displayName": "Exchange Protection Policy",
  "status": "inactive",
  "createdBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "email": "User1@contoso.com",
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "User1"
    }
  },
  "createdDateTime": "2015-06-19T12:01:03.45Z",
  "lastModifiedBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "email": "User2@constoso.com",
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "User2"
    }
  },
  "lastModifiedDateTime": "2015-06-19T12:01:03.45Z",
  "retentionSettings": [
    {
      "interval": "R/PT10M",
      "period": "P14D"
    },
    {
      "interval": "R/P1W",
      "period": "P180D"
    }
  ]
}
```
