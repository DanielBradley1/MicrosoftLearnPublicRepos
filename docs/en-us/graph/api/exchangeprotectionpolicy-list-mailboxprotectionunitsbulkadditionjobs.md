<!-- Source: https://learn.microsoft.com/en-us/graph/api/exchangeprotectionpolicy-list-mailboxprotectionunitsbulkadditionjobs?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List mailboxProtectionUnitsBulkAdditionJobs

Namespace: microsoft.graph

Get a list of [mailboxProtectionUnitsBulkAdditionJobs](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunitsbulkadditionjob?view=graph-rest-1.0) objects associated with an [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0).

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
GET /solutions/backupRestore/exchangeProtectionPolicies/{exchangeProtectionPolicyId}/mailboxProtectionUnitsBulkAdditionJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a list of [mailboxProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunitsbulkadditionjob?view=graph-rest-1.0) objects in the response body. The `mailboxes` and `directoryObjectIds` fields are omitted from the response body in order to limit the response size.

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

```http
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/mailboxProtectionUnitsBulkAdditionJobs
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ExchangeProtectionPolicies["{exchangeProtectionPolicy-id}"].MailboxProtectionUnitsBulkAdditionJobs.GetAsync();
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
mailboxProtectionUnitsBulkAdditionJobs, err := graphClient.Solutions().BackupRestore().ExchangeProtectionPolicies().ByExchangeProtectionPolicyId("exchangeProtectionPolicy-id").MailboxProtectionUnitsBulkAdditionJobs().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxProtectionUnitsBulkAdditionJobCollectionResponse result = graphClient.solutions().backupRestore().exchangeProtectionPolicies().byExchangeProtectionPolicyId("{exchangeProtectionPolicy-id}").mailboxProtectionUnitsBulkAdditionJobs().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let mailboxProtectionUnitsBulkAdditionJobs = await client.api('/solutions/backupRestore/exchangeProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/mailboxProtectionUnitsBulkAdditionJobs')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->backupRestore()->exchangeProtectionPolicies()->byExchangeProtectionPolicyId('exchangeProtectionPolicy-id')->mailboxProtectionUnitsBulkAdditionJobs()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Get-MgSolutionBackupRestoreExchangeProtectionPolicyMailboxProtectionUnitBulkAdditionJob -ExchangeProtectionPolicyId $exchangeProtectionPolicyId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.backup_restore.exchange_protection_policies.by_exchange_protection_policy_id('exchangeProtectionPolicy-id').mailbox_protection_units_bulk_addition_jobs.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/mailboxProtectionUnitsBulkAdditionJobs

{
   "@odata.type": "#collection(microsoft.graph.mailboxProtectionUnitsBulkAdditionJob)",
   "@odata.context": "/solutions/backupRestore/exchangeProtectionPolicies('71633878-8321-4950-bfaf-ed285bdd1461')/mailboxProtectionUnitsBulkAdditionJobs",
   "@odata.nextLink": "/solutions/backupRestore/exchangeProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/mailboxProtectionUnitsBulkAdditionJobs?$top=3&$skiptoken=M2UyZDAwMDAwMDMxMzkzYTMyNjQ2MTM0NjMzMjM5NjYzNjY0MzczMDM0MzE2NTYzNjEzNzMwNjIzNjMzMzg2MjM0MzM2NDM0MzUzNDMzMzc0MDc0Njg3MjY1NjE2NDJlNzYzMjAxZThmYjY4M2Y3ODAxMDAwMDg4NjA5ODdhNzgwMTAwMDB8MTYxNjk2NDUwOTgzMg%3d%3d",
   "value":
   [
      {
         "@odata.type": "#microsoft.graph.mailboxProtectionUnitsBulkAdditionJob",
         "displayName" : "Mailbox-I",
         "id":"61633878-8321-4950-bfaf-ed285bdd1461",
         "status" : "Completed",
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
         "lastModifiedDateTime":"2015-06-19T12-01-03.45Z"
      },
      {
         "@odata.type": "#microsoft.graph.mailboxProtectionUnitsBulkAdditionJob",
         "id":"61633878-8321-4950-bfaf-ed285bdd1461",
         "displayName" : "Mailbox-II",
         "status" : "CompletedWithErrors",
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
          "code" : "ProtectionResourcesNotFound",
          "message": "Errors while resolving protection resources",
          "details": 
              [
                  {
                      "code": "EmailNotFound",
                      "message": "Email address 'test1@microsoft.com' not found in directory",
                      "target" : "test1@microsoft.com"
                  },
                  {
                      "code": "EmailNotFound",
                      "message": "Email address 'test2@microsoft.com' not found in directory",
                      "target" : "test2@microsoft.com"
                  },
                  {
                      "code": "EmailNotFound",
                      "message": "Email address 'test3@microsoft.com' not found in directory",
                      "target" : "test3@microsoft.com"
                  }
              ]   
          }
      }
   ]
}
```
