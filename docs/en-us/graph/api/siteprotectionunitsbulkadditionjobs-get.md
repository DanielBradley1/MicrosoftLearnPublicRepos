<!-- Source: https://learn.microsoft.com/en-us/graph/api/siteprotectionunitsbulkadditionjobs-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get siteProtectionUnitsBulkAdditionJob

Namespace: microsoft.graph

Get a [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0) object by the ID associated with a [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

## HTTP request

```http
GET /solutions/backupRestore/sharePointProtectionPolicies/{sharePointProtectionPolicyId}/siteProtectionUnitsBulkAdditionJobs/{siteProtectionUnitsBulkAdditionJobId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteProtectionUnitsBulkAdditionJobs/71633878-8321-4950-bfaf-ed285bdd1461
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.SharePointProtectionPolicies["{sharePointProtectionPolicy-id}"].SiteProtectionUnitsBulkAdditionJobs["{siteProtectionUnitsBulkAdditionJob-id}"].GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
siteProtectionUnitsBulkAdditionJobs, err := graphClient.Solutions().BackupRestore().SharePointProtectionPolicies().BySharePointProtectionPolicyId("sharePointProtectionPolicy-id").SiteProtectionUnitsBulkAdditionJobs().BySiteProtectionUnitsBulkAdditionJobId("siteProtectionUnitsBulkAdditionJob-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SiteProtectionUnitsBulkAdditionJob result = graphClient.solutions().backupRestore().sharePointProtectionPolicies().bySharePointProtectionPolicyId("{sharePointProtectionPolicy-id}").siteProtectionUnitsBulkAdditionJobs().bySiteProtectionUnitsBulkAdditionJobId("{siteProtectionUnitsBulkAdditionJob-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let siteProtectionUnitsBulkAdditionJob = await client.api('/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteProtectionUnitsBulkAdditionJobs/71633878-8321-4950-bfaf-ed285bdd1461')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->backupRestore()->sharePointProtectionPolicies()->bySharePointProtectionPolicyId('sharePointProtectionPolicy-id')->siteProtectionUnitsBulkAdditionJobs()->bySiteProtectionUnitsBulkAdditionJobId('siteProtectionUnitsBulkAdditionJob-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Get-MgSolutionBackupRestoreSharePointProtectionPolicySiteProtectionUnitBulkAdditionJob -SharePointProtectionPolicyId $sharePointProtectionPolicyId -SiteProtectionUnitsBulkAdditionJobId $siteProtectionUnitsBulkAdditionJobId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.backup_restore.share_point_protection_policies.by_share_point_protection_policy_id('sharePointProtectionPolicy-id').site_protection_units_bulk_addition_jobs.by_site_protection_units_bulk_addition_job_id('siteProtectionUnitsBulkAdditionJob-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteProtectionUnitsBulkAdditionJobs/61633878-8321-4950-bfaf-ed285bdd1461

{
   "@odata.type": "#microsoft.graph.siteProtectionUnitsBulkAdditionJob",
   "id":"61633878-8321-4950-bfaf-ed285bdd1461",
   "displayName" : "Sites-I",
   "status" : "completedWithErrors",
    "siteWebUrls":  [ "https://contoso1@sharepoint.com", "https://contoso2@sharepoint.com", "https://contoso3@sharepoint.com", "https://contoso4@sharepoint.com", "https://testSite1.sharepoint.com", "https://testSite2.sharepoint.com", "https://testSite3.sharepoint.com" ],
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
    "error":{
    "details": 
        [
            {
                "code": "SiteUrlNotFound",
                "message": "Site Url 'https://testSite1.sharepoint.com' could not be resolved"
            },
            {
                "code": "SiteUrlNotFound",
                "message": "Site Url 'https://testSite2.sharepoint.com' could not be resolved"
            },
            {
                "code": "SiteUrlNotFound",
                "message": "Site Url 'https://testSite3.sharepoint.com' could not be resolved"
            }
        ]   
    }       
}
```
