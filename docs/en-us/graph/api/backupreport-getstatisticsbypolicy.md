<!-- Source: https://learn.microsoft.com/en-us/graph/api/backupreport-getstatisticsbypolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# backupReport: getStatisticsByPolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the statistics that correspond to the specified policy ID of a [backupPolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/backuppolicyreport?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Configuration.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Configuration.Read.All | Not available. |

## HTTP request

```http
GET /solutions/backupRestore/reports/getStatisticsByPolicy(policyId='{backupPolicyId}')
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `policyId` | String | The ID of the backup policy for which the report is requested. Required. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [backupPolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/backuppolicyreport?view=graph-rest-beta) in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/solutions/backupRestore/reports/getStatisticsByPolicy(policyId='98a71fd2-00f7-413f-a908-370acfb2983f')
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.backupPolicyReport",
  "backupPolicyId": "98a71fd2-00f7-413f-a908-370acfb2983f",
  "displayName": "Exchange Policy - Inadvertent data loss",
  "countStatistics": {
    "total": 5,
    "protectedInProgress": 0,
    "unprotectedInProgress": 0,
    "protectedCompleted": 0,
    "unprotectedCompleted": 0,
    "protectedFailed": 5,
    "unprotectedFailed": 0,
    "removed": null,
    "offboardRequested": 0,
    "lastComputedDateTime": "2026-01-16T09:48:48.5534369Z"
  }
}
```
