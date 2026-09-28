<!-- Source: https://learn.microsoft.com/en-us/graph/api/siteprotectionunitsbulkadditionjobs-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-03 -->

# Create siteProtectionUnitsBulkAdditionJob

Namespace: microsoft.graph

Create a [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0) object associated with a [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0).

The initial status upon creation of the job is `active`. When all the `siteUrls` and `siteIds` are added into the corresponding SharePoint protection policy, the status of job is `completed`.

If any failures occur, the status of the job is `completedWithErrors`.

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
POST   /solutions/backupRestore/sharePointProtectionPolicies/{sharePointProtectionPolicyId}/siteProtectionUnitsBulkAdditionJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, include a JSON representation of the [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteProtectionUnitsBulkAdditionJobs 
Content-Type: application/json

{
   "displayName" : "Sites-I",
   "siteWebUrls" : [ "https://contoso.sharepoint.com/test1", "https://contoso.sharepoint.com/test2", "https://contoso.sharepoint.com/test4", "https://contoso.sharepoint.com/test5" ],
   "siteIds" : [ "contoso.sharepoint.com,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee4532", "contoso.sharepoint.com,ab60e844-ba1d-49bc-b4d4-d5e36bae9019,832a596e-90a1-49e3-9b48-bfa80bee4532"]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const siteProtectionUnitsBulkAdditionJob = {
   displayName: 'Sites-I',
   siteWebUrls: [ 'https://contoso.sharepoint.com/test1', 'https://contoso.sharepoint.com/test2', 'https://contoso.sharepoint.com/test4', 'https://contoso.sharepoint.com/test5' ],
   siteIds: [ 'contoso.sharepoint.com,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee4532', 'contoso.sharepoint.com,ab60e844-ba1d-49bc-b4d4-d5e36bae9019,832a596e-90a1-49e3-9b48-bfa80bee4532']
};

await client.api('/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteProtectionUnitsBulkAdditionJobs')
	.post(siteProtectionUnitsBulkAdditionJob);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
   "@odata.type": "#microsoft.graph.siteProtectionUnitsBulkAdditionJob",
   "id" :"71633878-8321-4950-bfaf-ed285bdd1461",
   "displayName" : "Sites-I",
   "status" : "active",
    "siteWebUrls" : [ "https://contoso.sharepoint.com/test1", "https://contoso.sharepoint.com/test2", "https://contoso.sharepoint.com/test4", "https://contoso.sharepoint.com/test5" ],
    "siteIds" : [ "contoso.sharepoint.com,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee4532", "contoso.sharepoint.com,ab60e844-ba1d-49bc-b4d4-d5e36bae9019,832a596e-90a1-49e3-9b48-bfa80bee4532"],
   "createdBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "user":{
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
      }
   },
   "createdDateTime":"2015-06-19T12-01-03.45Z",
   "lastModifiedBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "user":{
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
      }
   },
   "lastModifiedDateTime":"2015-06-19T12-01-03.45Z",
}
```
