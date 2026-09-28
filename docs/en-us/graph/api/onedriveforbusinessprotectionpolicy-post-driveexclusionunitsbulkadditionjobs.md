<!-- Source: https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessprotectionpolicy-post-driveexclusionunitsbulkadditionjobs?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Create driveExclusionUnitsBulkAdditionJob

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [drive exclusion units bulk addition job](https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunitsbulkadditionjob?view=graph-rest-beta) for a [OneDrive for work or school protection policy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-beta).

The initial status upon creation of the job is `active`. When all the **drives** are added to the corresponding OneDrive for work or school protection policy as exclusion units, the status of the job is `completed`. If any failures occur, the status of the job is `completedWithErrors`.

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
POST /solutions/backupRestore/oneDriveForBusinessProtectionPolicies/{oneDriveForBusinessProtectionPolicyId}/driveExclusionUnitsBulkAdditionJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, include a JSON representation of the [driveExclusionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunitsbulkadditionjob?view=graph-rest-beta) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the bulk addition job. Required. |
| drives | String collection | The email addresses or user principal names of the users whose OneDrive drives are to be added as exclusion units. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [driveExclusionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunitsbulkadditionjob?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e/driveExclusionUnitsBulkAdditionJobs
Content-Type: application/json

{
  "displayName": "Bulk exclude contractor drives",
  "drives": [
    "contractor1@contoso.com",
    "contractor2@contoso.com",
    "contractor3@contoso.com"
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const driveExclusionUnitsBulkAdditionJob = {
  displayName: 'Bulk exclude contractor drives',
  drives: [
    'contractor1@contoso.com',
    'contractor2@contoso.com',
    'contractor3@contoso.com'
  ]
};

await client.api('/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e/driveExclusionUnitsBulkAdditionJobs')
	.version('beta')
	.post(driveExclusionUnitsBulkAdditionJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#solutions/backupRestore/oneDriveForBusinessProtectionPolicies('845457dc-4bb2-4815-bef3-8628ebd1952e')/driveExclusionUnitsBulkAdditionJobs/$entity",
  "id": "4b014d8c-71fe-4d00-a01a-31850bc5b32c",
  "displayName": "Bulk exclude contractor drives",
  "status": "active",
  "drives": [
    "contractor1@contoso.com",
    "contractor2@contoso.com",
    "contractor3@contoso.com"
  ],
  "createdDateTime": "2026-02-16T14:00:00Z",
  "lastModifiedDateTime": "2026-02-16T14:00:00Z",
  "createdBy": {
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e"
    }
  },
  "lastModifiedBy": {
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e"
    }
  }
}
```
