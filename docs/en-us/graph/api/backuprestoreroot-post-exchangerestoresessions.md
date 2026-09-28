<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-exchangerestoresessions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create exchangeRestoreSession

Namespace: microsoft.graph

Create a new [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.ReadWrite.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/exchangeRestoreSessions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0).

You can specify the following properties when you create an **exchangeRestoreSession** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| granularMailboxRestoreArtifact | [granularMailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularmailboxrestoreartifact?view=graph-rest-1.0) collection | Collection of [granularMailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularmailboxrestoreartifact?view=graph-rest-1.0) objects. |
| mailboxRestoreArtifacts | [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) collection | Collection of [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) objects. |

## Response

If successful, this method returns a `201 Created` response code and an [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Create exchangeRestoreSession with mailboxRestoreArtifacts

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeRestoreSessions
Content-Type: application/json

{
  "mailboxRestoreArtifacts": [
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279" },
      "destinationType": "inPlace"
    },
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888280" },
      "destinationType": "inPlace"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ExchangeRestoreSession
{
	MailboxRestoreArtifacts = new List<MailboxRestoreArtifact>
	{
		new MailboxRestoreArtifact
		{
			RestorePoint = new RestorePoint
			{
				Id = "1f1fccc3-a642-4f61-bf49-f37b9a888279",
			},
			DestinationType = DestinationType.InPlace,
		},
		new MailboxRestoreArtifact
		{
			RestorePoint = new RestorePoint
			{
				Id = "1f1fccc3-a642-4f61-bf49-f37b9a888280",
			},
			DestinationType = DestinationType.InPlace,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ExchangeRestoreSessions.PostAsync(requestBody);
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

requestBody := graphmodels.NewExchangeRestoreSession()


mailboxRestoreArtifact := graphmodels.NewMailboxRestoreArtifact()
restorePoint := graphmodels.NewRestorePoint()
id := "1f1fccc3-a642-4f61-bf49-f37b9a888279"
restorePoint.SetId(&id) 
mailboxRestoreArtifact.SetRestorePoint(restorePoint)
destinationType := graphmodels.INPLACE_DESTINATIONTYPE 
mailboxRestoreArtifact.SetDestinationType(&destinationType) 
mailboxRestoreArtifact1 := graphmodels.NewMailboxRestoreArtifact()
restorePoint := graphmodels.NewRestorePoint()
id := "1f1fccc3-a642-4f61-bf49-f37b9a888280"
restorePoint.SetId(&id) 
mailboxRestoreArtifact1.SetRestorePoint(restorePoint)
destinationType := graphmodels.INPLACE_DESTINATIONTYPE 
mailboxRestoreArtifact1.SetDestinationType(&destinationType) 

mailboxRestoreArtifacts := []graphmodels.MailboxRestoreArtifactable {
	mailboxRestoreArtifact,
	mailboxRestoreArtifact1,
}
requestBody.SetMailboxRestoreArtifacts(mailboxRestoreArtifacts)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exchangeRestoreSessions, err := graphClient.Solutions().BackupRestore().ExchangeRestoreSessions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExchangeRestoreSession exchangeRestoreSession = new ExchangeRestoreSession();
LinkedList<MailboxRestoreArtifact> mailboxRestoreArtifacts = new LinkedList<MailboxRestoreArtifact>();
MailboxRestoreArtifact mailboxRestoreArtifact = new MailboxRestoreArtifact();
RestorePoint restorePoint = new RestorePoint();
restorePoint.setId("1f1fccc3-a642-4f61-bf49-f37b9a888279");
mailboxRestoreArtifact.setRestorePoint(restorePoint);
mailboxRestoreArtifact.setDestinationType(DestinationType.InPlace);
mailboxRestoreArtifacts.add(mailboxRestoreArtifact);
MailboxRestoreArtifact mailboxRestoreArtifact1 = new MailboxRestoreArtifact();
RestorePoint restorePoint1 = new RestorePoint();
restorePoint1.setId("1f1fccc3-a642-4f61-bf49-f37b9a888280");
mailboxRestoreArtifact1.setRestorePoint(restorePoint1);
mailboxRestoreArtifact1.setDestinationType(DestinationType.InPlace);
mailboxRestoreArtifacts.add(mailboxRestoreArtifact1);
exchangeRestoreSession.setMailboxRestoreArtifacts(mailboxRestoreArtifacts);
ExchangeRestoreSession result = graphClient.solutions().backupRestore().exchangeRestoreSessions().post(exchangeRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exchangeRestoreSession = {
  mailboxRestoreArtifacts: [
    {
      restorePoint: { id: '1f1fccc3-a642-4f61-bf49-f37b9a888279' },
      destinationType: 'inPlace'
    },
    {
      restorePoint: { id: '1f1fccc3-a642-4f61-bf49-f37b9a888280' },
      destinationType: 'inPlace'
    }
  ]
};

await client.api('/solutions/backupRestore/exchangeRestoreSessions')
	.post(exchangeRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExchangeRestoreSession;
use Microsoft\Graph\Generated\Models\MailboxRestoreArtifact;
use Microsoft\Graph\Generated\Models\RestorePoint;
use Microsoft\Graph\Generated\Models\DestinationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExchangeRestoreSession();
$mailboxRestoreArtifactsMailboxRestoreArtifact1 = new MailboxRestoreArtifact();
$mailboxRestoreArtifactsMailboxRestoreArtifact1RestorePoint = new RestorePoint();
$mailboxRestoreArtifactsMailboxRestoreArtifact1RestorePoint->setId('1f1fccc3-a642-4f61-bf49-f37b9a888279');
$mailboxRestoreArtifactsMailboxRestoreArtifact1->setRestorePoint($mailboxRestoreArtifactsMailboxRestoreArtifact1RestorePoint);
$mailboxRestoreArtifactsMailboxRestoreArtifact1->setDestinationType(new DestinationType('inPlace'));
$mailboxRestoreArtifactsArray []= $mailboxRestoreArtifactsMailboxRestoreArtifact1;
$mailboxRestoreArtifactsMailboxRestoreArtifact2 = new MailboxRestoreArtifact();
$mailboxRestoreArtifactsMailboxRestoreArtifact2RestorePoint = new RestorePoint();
$mailboxRestoreArtifactsMailboxRestoreArtifact2RestorePoint->setId('1f1fccc3-a642-4f61-bf49-f37b9a888280');
$mailboxRestoreArtifactsMailboxRestoreArtifact2->setRestorePoint($mailboxRestoreArtifactsMailboxRestoreArtifact2RestorePoint);
$mailboxRestoreArtifactsMailboxRestoreArtifact2->setDestinationType(new DestinationType('inPlace'));
$mailboxRestoreArtifactsArray []= $mailboxRestoreArtifactsMailboxRestoreArtifact2;
$requestBody->setMailboxRestoreArtifacts($mailboxRestoreArtifactsArray);


$result = $graphServiceClient->solutions()->backupRestore()->exchangeRestoreSessions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	mailboxRestoreArtifacts = @(
		@{
			restorePoint = @{
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888279"
			}
			destinationType = "inPlace"
		}
		@{
			restorePoint = @{
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888280"
			}
			destinationType = "inPlace"
		}
	)
}

New-MgSolutionBackupRestoreExchangeRestoreSession -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.exchange_restore_session import ExchangeRestoreSession
from msgraph.generated.models.mailbox_restore_artifact import MailboxRestoreArtifact
from msgraph.generated.models.restore_point import RestorePoint
from msgraph.generated.models.destination_type import DestinationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExchangeRestoreSession(
	mailbox_restore_artifacts = [
		MailboxRestoreArtifact(
			restore_point = RestorePoint(
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888279",
			),
			destination_type = DestinationType.InPlace,
		),
		MailboxRestoreArtifact(
			restore_point = RestorePoint(
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888280",
			),
			destination_type = DestinationType.InPlace,
		),
	],
)

result = await graph_client.solutions.backup_restore.exchange_restore_sessions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#exchangeRestoreSessions/$entity",
  "id": "959ba739-70b5-43c4-8c90-b2c22014f18b",
  "status": "draft",
  "restoreJobType": "standard",
  "restoreSessionArtifactCount": {
    "total": 2,
    "completed": 0,
    "inProgress": 0,
    "failed": 0
  },
  "createdBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "ABC"
    }
  },
  "createdDateTime": "2023-03-30T12:01:03.45Z",
  "lastModifiedBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "DEF"
    }
  },
  "lastModifiedDateTime": "2023-03-30T12:01:03.45Z",
  "error": null
}
```

### Example 2: Create exchangeRestoreSession with granularMailboxRestoreArtifact

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeRestoreSessions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.exchangeRestoreSession",
  "granularMailboxRestoreArtifacts": [
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279" },
      "destinationType": "inPlace",
      "searchResponseId" : "M2UyZDAwMDAwMDMxMzkzYTMyNj"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ExchangeRestoreSession
{
	OdataType = "#microsoft.graph.exchangeRestoreSession",
	GranularMailboxRestoreArtifacts = new List<GranularMailboxRestoreArtifact>
	{
		new GranularMailboxRestoreArtifact
		{
			RestorePoint = new RestorePoint
			{
				Id = "1f1fccc3-a642-4f61-bf49-f37b9a888279",
			},
			DestinationType = DestinationType.InPlace,
			SearchResponseId = "M2UyZDAwMDAwMDMxMzkzYTMyNj",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ExchangeRestoreSessions.PostAsync(requestBody);
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

requestBody := graphmodels.NewExchangeRestoreSession()


granularMailboxRestoreArtifact := graphmodels.NewGranularMailboxRestoreArtifact()
restorePoint := graphmodels.NewRestorePoint()
id := "1f1fccc3-a642-4f61-bf49-f37b9a888279"
restorePoint.SetId(&id) 
granularMailboxRestoreArtifact.SetRestorePoint(restorePoint)
destinationType := graphmodels.INPLACE_DESTINATIONTYPE 
granularMailboxRestoreArtifact.SetDestinationType(&destinationType) 
searchResponseId := "M2UyZDAwMDAwMDMxMzkzYTMyNj"
granularMailboxRestoreArtifact.SetSearchResponseId(&searchResponseId) 

granularMailboxRestoreArtifacts := []graphmodels.GranularMailboxRestoreArtifactable {
	granularMailboxRestoreArtifact,
}
requestBody.SetGranularMailboxRestoreArtifacts(granularMailboxRestoreArtifacts)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exchangeRestoreSessions, err := graphClient.Solutions().BackupRestore().ExchangeRestoreSessions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExchangeRestoreSession exchangeRestoreSession = new ExchangeRestoreSession();
exchangeRestoreSession.setOdataType("#microsoft.graph.exchangeRestoreSession");
LinkedList<GranularMailboxRestoreArtifact> granularMailboxRestoreArtifacts = new LinkedList<GranularMailboxRestoreArtifact>();
GranularMailboxRestoreArtifact granularMailboxRestoreArtifact = new GranularMailboxRestoreArtifact();
RestorePoint restorePoint = new RestorePoint();
restorePoint.setId("1f1fccc3-a642-4f61-bf49-f37b9a888279");
granularMailboxRestoreArtifact.setRestorePoint(restorePoint);
granularMailboxRestoreArtifact.setDestinationType(DestinationType.InPlace);
granularMailboxRestoreArtifact.setSearchResponseId("M2UyZDAwMDAwMDMxMzkzYTMyNj");
granularMailboxRestoreArtifacts.add(granularMailboxRestoreArtifact);
exchangeRestoreSession.setGranularMailboxRestoreArtifacts(granularMailboxRestoreArtifacts);
ExchangeRestoreSession result = graphClient.solutions().backupRestore().exchangeRestoreSessions().post(exchangeRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exchangeRestoreSession = {
  '@odata.type': '#microsoft.graph.exchangeRestoreSession',
  granularMailboxRestoreArtifacts: [
    {
      restorePoint: { id: '1f1fccc3-a642-4f61-bf49-f37b9a888279' },
      destinationType: 'inPlace',
      searchResponseId: 'M2UyZDAwMDAwMDMxMzkzYTMyNj'
    }
  ]
};

await client.api('/solutions/backupRestore/exchangeRestoreSessions')
	.post(exchangeRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExchangeRestoreSession;
use Microsoft\Graph\Generated\Models\GranularMailboxRestoreArtifact;
use Microsoft\Graph\Generated\Models\RestorePoint;
use Microsoft\Graph\Generated\Models\DestinationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExchangeRestoreSession();
$requestBody->setOdataType('#microsoft.graph.exchangeRestoreSession');
$granularMailboxRestoreArtifactsGranularMailboxRestoreArtifact1 = new GranularMailboxRestoreArtifact();
$granularMailboxRestoreArtifactsGranularMailboxRestoreArtifact1RestorePoint = new RestorePoint();
$granularMailboxRestoreArtifactsGranularMailboxRestoreArtifact1RestorePoint->setId('1f1fccc3-a642-4f61-bf49-f37b9a888279');
$granularMailboxRestoreArtifactsGranularMailboxRestoreArtifact1->setRestorePoint($granularMailboxRestoreArtifactsGranularMailboxRestoreArtifact1RestorePoint);
$granularMailboxRestoreArtifactsGranularMailboxRestoreArtifact1->setDestinationType(new DestinationType('inPlace'));
$granularMailboxRestoreArtifactsGranularMailboxRestoreArtifact1->setSearchResponseId('M2UyZDAwMDAwMDMxMzkzYTMyNj');
$granularMailboxRestoreArtifactsArray []= $granularMailboxRestoreArtifactsGranularMailboxRestoreArtifact1;
$requestBody->setGranularMailboxRestoreArtifacts($granularMailboxRestoreArtifactsArray);


$result = $graphServiceClient->solutions()->backupRestore()->exchangeRestoreSessions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	"@odata.type" = "#microsoft.graph.exchangeRestoreSession"
	granularMailboxRestoreArtifacts = @(
		@{
			restorePoint = @{
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888279"
			}
			destinationType = "inPlace"
			searchResponseId = "M2UyZDAwMDAwMDMxMzkzYTMyNj"
		}
	)
}

New-MgSolutionBackupRestoreExchangeRestoreSession -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.exchange_restore_session import ExchangeRestoreSession
from msgraph.generated.models.granular_mailbox_restore_artifact import GranularMailboxRestoreArtifact
from msgraph.generated.models.restore_point import RestorePoint
from msgraph.generated.models.destination_type import DestinationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExchangeRestoreSession(
	odata_type = "#microsoft.graph.exchangeRestoreSession",
	granular_mailbox_restore_artifacts = [
		GranularMailboxRestoreArtifact(
			restore_point = RestorePoint(
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888279",
			),
			destination_type = DestinationType.InPlace,
			search_response_id = "M2UyZDAwMDAwMDMxMzkzYTMyNj",
		),
	],
)

result = await graph_client.solutions.backup_restore.exchange_restore_sessions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#exchangeRestoreSessions/$entity",
  "id": "959ba739-70b5-43c4-8c90-b2c22014f18b",
  "status": "draft",
  "restoreJobType": "standard",
  "restoreSessionArtifactCount": {
    "total": 2,
    "completed": 0,
    "inProgress": 0,
    "failed": 0
  },
  "createdBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "ABC"
    }
  },
  "createdDateTime": "2023-03-30T12:01:03.45Z",
  "lastModifiedBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "DEF"
    }
  },
  "lastModifiedDateTime": "2023-03-30T12:01:03.45Z",
  "error": null,
  "granularMailboxRestoreArtifact": [
    {
      "id": "959ba739-70b5-43c4-8c90-b2c22014f18a",
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279" },
      "restoredFolderId": null,
      "status": "added",
      "startDateTime": null,
      "destinationType": "inPlace",
      "searchResponseId": "M2UyZDAwMDAwMDMxMzkzYTMyNj",
      "error": null
    }
  ]
}
```
