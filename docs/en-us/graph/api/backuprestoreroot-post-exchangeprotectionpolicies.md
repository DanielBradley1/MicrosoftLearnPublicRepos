<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-exchangeprotectionpolicies?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-11 -->

# Create exchangeProtectionPolicy

Namespace: microsoft.graph

Create a protection policy for the Exchange service in a Microsoft 365 tenant. The policy is set to `inactive` when it is created. Users can also provide a list of protection units under the policy.

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

## Request body

In the request body, include a JSON representation of the [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0) object You can specify the following properties when you create an **exchangeProtectionPolicy** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the Exchange Protection Policy. |
| mailboxProtectionUnits | Collection\([mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0)\) | Collection of the mailboxProtectionUnits to be added to the exchangeProtectionPolicy. |

## Response

If successful, this method returns a `201 Created` response code and an [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies

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
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ExchangeProtectionPolicy
{
	DisplayName = "Exchange Protection Policy",
	MailboxProtectionUnits = new List<MailboxProtectionUnit>
	{
		new MailboxProtectionUnit
		{
			DirectoryObjectId = "cdd3a849-dcaf-4a85-af82-7e39fc14019a",
		},
		new MailboxProtectionUnit
		{
			DirectoryObjectId = "9bc069da-b746-41a4-89ab-26125c6373c7",
		},
		new MailboxProtectionUnit
		{
			DirectoryObjectId = "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ExchangeProtectionPolicies.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewExchangeProtectionPolicy()
displayName := "Exchange Protection Policy"
requestBody.SetDisplayName(&displayName) 


mailboxProtectionUnit := graphmodels.NewMailboxProtectionUnit()
directoryObjectId := "cdd3a849-dcaf-4a85-af82-7e39fc14019a"
mailboxProtectionUnit.SetDirectoryObjectId(&directoryObjectId) 
mailboxProtectionUnit1 := graphmodels.NewMailboxProtectionUnit()
directoryObjectId := "9bc069da-b746-41a4-89ab-26125c6373c7"
mailboxProtectionUnit1.SetDirectoryObjectId(&directoryObjectId) 
mailboxProtectionUnit2 := graphmodels.NewMailboxProtectionUnit()
directoryObjectId := "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7"
mailboxProtectionUnit2.SetDirectoryObjectId(&directoryObjectId) 

mailboxProtectionUnits := []graphmodels.MailboxProtectionUnitable {
	mailboxProtectionUnit,
	mailboxProtectionUnit1,
	mailboxProtectionUnit2,
}
requestBody.SetMailboxProtectionUnits(mailboxProtectionUnits)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exchangeProtectionPolicies, err := graphClient.Solutions().BackupRestore().ExchangeProtectionPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExchangeProtectionPolicy exchangeProtectionPolicy = new ExchangeProtectionPolicy();
exchangeProtectionPolicy.setDisplayName("Exchange Protection Policy");
LinkedList<MailboxProtectionUnit> mailboxProtectionUnits = new LinkedList<MailboxProtectionUnit>();
MailboxProtectionUnit mailboxProtectionUnit = new MailboxProtectionUnit();
mailboxProtectionUnit.setDirectoryObjectId("cdd3a849-dcaf-4a85-af82-7e39fc14019a");
mailboxProtectionUnits.add(mailboxProtectionUnit);
MailboxProtectionUnit mailboxProtectionUnit1 = new MailboxProtectionUnit();
mailboxProtectionUnit1.setDirectoryObjectId("9bc069da-b746-41a4-89ab-26125c6373c7");
mailboxProtectionUnits.add(mailboxProtectionUnit1);
MailboxProtectionUnit mailboxProtectionUnit2 = new MailboxProtectionUnit();
mailboxProtectionUnit2.setDirectoryObjectId("b218eb4a-ea72-42bd-8f0b-d0bbf794bec7");
mailboxProtectionUnits.add(mailboxProtectionUnit2);
exchangeProtectionPolicy.setMailboxProtectionUnits(mailboxProtectionUnits);
ExchangeProtectionPolicy result = graphClient.solutions().backupRestore().exchangeProtectionPolicies().post(exchangeProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exchangeProtectionPolicy = {
  displayName: 'Exchange Protection Policy',
  mailboxProtectionUnits: [
    {
      directoryObjectId: 'cdd3a849-dcaf-4a85-af82-7e39fc14019a'
    },
    {
      directoryObjectId: '9bc069da-b746-41a4-89ab-26125c6373c7'
    },
    {
      directoryObjectId: 'b218eb4a-ea72-42bd-8f0b-d0bbf794bec7'
    }
  ]
};

await client.api('/solutions/backupRestore/exchangeProtectionPolicies')
	.post(exchangeProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExchangeProtectionPolicy;
use Microsoft\Graph\Generated\Models\MailboxProtectionUnit;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExchangeProtectionPolicy();
$requestBody->setDisplayName('Exchange Protection Policy');
$mailboxProtectionUnitsMailboxProtectionUnit1 = new MailboxProtectionUnit();
$mailboxProtectionUnitsMailboxProtectionUnit1->setDirectoryObjectId('cdd3a849-dcaf-4a85-af82-7e39fc14019a');
$mailboxProtectionUnitsArray []= $mailboxProtectionUnitsMailboxProtectionUnit1;
$mailboxProtectionUnitsMailboxProtectionUnit2 = new MailboxProtectionUnit();
$mailboxProtectionUnitsMailboxProtectionUnit2->setDirectoryObjectId('9bc069da-b746-41a4-89ab-26125c6373c7');
$mailboxProtectionUnitsArray []= $mailboxProtectionUnitsMailboxProtectionUnit2;
$mailboxProtectionUnitsMailboxProtectionUnit3 = new MailboxProtectionUnit();
$mailboxProtectionUnitsMailboxProtectionUnit3->setDirectoryObjectId('b218eb4a-ea72-42bd-8f0b-d0bbf794bec7');
$mailboxProtectionUnitsArray []= $mailboxProtectionUnitsMailboxProtectionUnit3;
$requestBody->setMailboxProtectionUnits($mailboxProtectionUnitsArray);


$result = $graphServiceClient->solutions()->backupRestore()->exchangeProtectionPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	displayName = "Exchange Protection Policy"
	mailboxProtectionUnits = @(
		@{
			directoryObjectId = "cdd3a849-dcaf-4a85-af82-7e39fc14019a"
		}
		@{
			directoryObjectId = "9bc069da-b746-41a4-89ab-26125c6373c7"
		}
		@{
			directoryObjectId = "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7"
		}
	)
}

New-MgSolutionBackupRestoreExchangeProtectionPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.exchange_protection_policy import ExchangeProtectionPolicy
from msgraph.generated.models.mailbox_protection_unit import MailboxProtectionUnit
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExchangeProtectionPolicy(
	display_name = "Exchange Protection Policy",
	mailbox_protection_units = [
		MailboxProtectionUnit(
			directory_object_id = "cdd3a849-dcaf-4a85-af82-7e39fc14019a",
		),
		MailboxProtectionUnit(
			directory_object_id = "9bc069da-b746-41a4-89ab-26125c6373c7",
		),
		MailboxProtectionUnit(
			directory_object_id = "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7",
		),
	],
)

result = await graph_client.solutions.backup_restore.exchange_protection_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/ProtectionPolicies/b218eb4a-ea72-42bd-8f0b-d0bbf794bec7

{
  "@odata.context": "/solutions/backupRestore/$metadata#exchangeProtectionPolicies/$entity",
  "id": "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7",
  "displayName": "SharePoint Protection Policy",
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
      "period": "P2W"
    },
    {
      "interval": "R/P1W",
      "period": "P1Y"
    }
  ]
}
```
