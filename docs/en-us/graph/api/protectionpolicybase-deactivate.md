<!-- Source: https://learn.microsoft.com/en-us/graph/api/protectionpolicybase-deactivate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-04 -->

# protectionPolicyBase: deactivate

Namespace: microsoft.graph

Deactivate a [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0).

When a protection policy is deactivated, backup activity stops immediately, no new backups are taken, and the protected resources are no longer covered by the policy. Any backups taken before deactivation are retained according to the retention policy, after which they're offboarded. You can restore data using previous restore points even after deactivation.

To reactivate a deactivated policy, use the [activate](https://learn.microsoft.com/en-us/graph/api/protectionpolicybase-activate?view=graph-rest-1.0) API.

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
POST /solutions/backupRestore/protectionPolicies/{protectionPolicyBaseId}/deactivate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `202 Accepted` response code and a [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Deactivate an active protection policy

Deactivating the protection policy when it is in active state.

#### Request

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/ProtectionPolicies/61633878-8321-4950-bfaf-ed285bdd1461/deactivate
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ProtectionPolicies["{protectionPolicyBase-id}"].Deactivate.PostAsync();
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
deactivate, err := graphClient.Solutions().BackupRestore().ProtectionPolicies().ByProtectionPolicyBaseId("protectionPolicyBase-id").Deactivate().Post(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.solutions().backupRestore().protectionPolicies().byProtectionPolicyBaseId("{protectionPolicyBase-id}").deactivate().post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/backupRestore/ProtectionPolicies/61633878-8321-4950-bfaf-ed285bdd1461/deactivate')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->backupRestore()->protectionPolicies()->byProtectionPolicyBaseId('protectionPolicyBase-id')->deactivate()->post()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Invoke-MgDeactivateSolutionBackupRestoreProtectionPolicy -ProtectionPolicyBaseId $protectionPolicyBaseId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.backup_restore.protection_policies.by_protection_policy_base_id('protectionPolicyBase-id').deactivate.post()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/protectionPolicies('61633878-8321-4950-bfaf-ed285bdd1461')

{
   "@odata.context":"/solutions/backupRestore/$metadata#ProtectionPolicies/$entity",
   "@odata.id":"/solutions/backupRestore/ProtectionPolicies(61633878-8321-4950-bfaf-ed285bdd1461)",
   "@odata.type": "#microsoft.graph.exchangeProtectionPolicy",
   "id":"61633878-8321-4950-bfaf-ed285bdd1461",
   "displayName":"Exchange Protection Policy",
   "status":"updating",
   "createdBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264",
         "displayName":"Microsoft Enhanced Restore"
      },
      "user":{
         "email":"ryan@contoso.com",
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e",
         "displayName":"Ryan"
      }
   },
   "createdDateTime":"2015-06-19T12:01:03.45Z",
   "lastModifiedBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264",
         "displayName":"Microsoft Enhanced Restore"
      },
      "user":{
         "email":"rian@contoso.com",
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e",
         "displayName":"Rian"
      }
   },
   "lastModifiedDateTime":"2015-06-19T12:01:03.45Z",
   "retentionSettings" : [
      {
          "interval": "R/PT10M",
          "period": "P2W"
      },
      {
          "interval": "R/P1W",
          "period": "P1Y"
      }
   ]
}
```

### Example 2 : Deactivate a protection policy in updating state

Deactivating the protection policy when it is in updating state.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/protectionPolicies/61633878-8321-4950-bfaf-ed285bdd1461/deactivate
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ProtectionPolicies["{protectionPolicyBase-id}"].Deactivate.PostAsync();
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
deactivate, err := graphClient.Solutions().BackupRestore().ProtectionPolicies().ByProtectionPolicyBaseId("protectionPolicyBase-id").Deactivate().Post(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.solutions().backupRestore().protectionPolicies().byProtectionPolicyBaseId("{protectionPolicyBase-id}").deactivate().post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/backupRestore/protectionPolicies/61633878-8321-4950-bfaf-ed285bdd1461/deactivate')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->backupRestore()->protectionPolicies()->byProtectionPolicyBaseId('protectionPolicyBase-id')->deactivate()->post()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Invoke-MgDeactivateSolutionBackupRestoreProtectionPolicy -ProtectionPolicyBaseId $protectionPolicyBaseId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.backup_restore.protection_policies.by_protection_policy_base_id('protectionPolicyBase-id').deactivate.post()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 400 Bad Request
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/ProtectionPolicies/61633878-8321-4950-bfaf-ed285bdd1461

{
  "error": {
    "code": "invalidStateForActivation",
    "message": "Policy in updating state, which is invalid for deactivation. Policy must be in Active or ActiveWithErrors state.",
    "innerError": {
      "date": "2023-03-03T07:15:31",
      "request-id": "7e921b55-8af4-41f5-881d-d425af822be0",
      "client-request-id": "77d27e8a-f18e-ce3a-42c9-f8a87fc00126"
    }
  }
}
```
