<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpc-sharesnapshot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-24 -->

# cloudPC: shareSnapshot

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Share a snapshot for a specific Cloud PC device.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/cloudPCs/{id}/shareSnapshot
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| cloudPcSnapshotId | String | The snapshot which will be copied to the customer's storage account. |
| storageAccountId | String | The storage account which receives the restore point \(snapshot\). |
| accessTier | [cloudPcBlobAccessTier](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkcreatesnapshot?view=graph-rest-beta#cloudpcblobaccesstier-values) | The access tier of the blob file that the snapshot is copied to. Possible values are `hot`, `cool`, `cold`, `archive`, and `unknownFutureValue`. The default value is `hot`. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPCs/b0a9cde2-e170-4dd9-97c3-ad1d3328a711/shareSnapshot
Content-Type: application/json

{
  "cloudPcSnapshotId": "A00009UV000_UniqueSubString",
  "storageAccountId": "/subscriptions/f68bd846-16ad-4b51-a7c6-c84944a3367c/resourceGroups/resourceGroupName/providers/Microsoft.Storage/storageAccounts/storageAccountName",
  "accessTier": "hot"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
