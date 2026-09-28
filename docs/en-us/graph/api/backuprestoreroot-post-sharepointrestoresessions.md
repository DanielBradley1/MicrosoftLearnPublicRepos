<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-sharepointrestoresessions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Create sharePointRestoreSession

Namespace: microsoft.graph

Create a new [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0) object. To create a granular restore session, granular site restore artifacts must be present in the payload. A request can't include both [granularSiteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularsiterestoreartifact?view=graph-rest-1.0) and [siteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifact?view=graph-rest-1.0) in the same **create** or **update** request.

If no payload is provided when you create the restore session, the request creates an empty `standard` restore session by default.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.ReadWrite.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/sharePointRestoreSessions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0).

You can specify the following properties when you create a **sharePointRestoreSession** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| siteRestoreArtifacts | [siteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifact?view=graph-rest-1.0) collection | A collection of [siteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifact?view=graph-rest-1.0) objects. Required. |
| granularSiteRestoreArtifacts | [granularSiteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularsiterestoreartifact?view=graph-rest-1.0) collection | A collection of [granularSiteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularsiterestoreartifact?view=graph-rest-1.0) objects. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Create a standard restore session

The following example shows how to create a standard restore session.

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointRestoreSessions
Content-Type: application/json

{
  "siteRestoreArtifacts": [
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

var requestBody = new SharePointRestoreSession
{
	SiteRestoreArtifacts = new List<SiteRestoreArtifact>
	{
		new SiteRestoreArtifact
		{
			RestorePoint = new RestorePoint
			{
				Id = "1f1fccc3-a642-4f61-bf49-f37b9a888279",
			},
			DestinationType = DestinationType.InPlace,
		},
		new SiteRestoreArtifact
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
var result = await graphClient.Solutions.BackupRestore.SharePointRestoreSessions.PostAsync(requestBody);
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

requestBody := graphmodels.NewSharePointRestoreSession()


siteRestoreArtifact := graphmodels.NewSiteRestoreArtifact()
restorePoint := graphmodels.NewRestorePoint()
id := "1f1fccc3-a642-4f61-bf49-f37b9a888279"
restorePoint.SetId(&id) 
siteRestoreArtifact.SetRestorePoint(restorePoint)
destinationType := graphmodels.INPLACE_DESTINATIONTYPE 
siteRestoreArtifact.SetDestinationType(&destinationType) 
siteRestoreArtifact1 := graphmodels.NewSiteRestoreArtifact()
restorePoint := graphmodels.NewRestorePoint()
id := "1f1fccc3-a642-4f61-bf49-f37b9a888280"
restorePoint.SetId(&id) 
siteRestoreArtifact1.SetRestorePoint(restorePoint)
destinationType := graphmodels.INPLACE_DESTINATIONTYPE 
siteRestoreArtifact1.SetDestinationType(&destinationType) 

siteRestoreArtifacts := []graphmodels.SiteRestoreArtifactable {
	siteRestoreArtifact,
	siteRestoreArtifact1,
}
requestBody.SetSiteRestoreArtifacts(siteRestoreArtifacts)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sharePointRestoreSessions, err := graphClient.Solutions().BackupRestore().SharePointRestoreSessions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointRestoreSession sharePointRestoreSession = new SharePointRestoreSession();
LinkedList<SiteRestoreArtifact> siteRestoreArtifacts = new LinkedList<SiteRestoreArtifact>();
SiteRestoreArtifact siteRestoreArtifact = new SiteRestoreArtifact();
RestorePoint restorePoint = new RestorePoint();
restorePoint.setId("1f1fccc3-a642-4f61-bf49-f37b9a888279");
siteRestoreArtifact.setRestorePoint(restorePoint);
siteRestoreArtifact.setDestinationType(DestinationType.InPlace);
siteRestoreArtifacts.add(siteRestoreArtifact);
SiteRestoreArtifact siteRestoreArtifact1 = new SiteRestoreArtifact();
RestorePoint restorePoint1 = new RestorePoint();
restorePoint1.setId("1f1fccc3-a642-4f61-bf49-f37b9a888280");
siteRestoreArtifact1.setRestorePoint(restorePoint1);
siteRestoreArtifact1.setDestinationType(DestinationType.InPlace);
siteRestoreArtifacts.add(siteRestoreArtifact1);
sharePointRestoreSession.setSiteRestoreArtifacts(siteRestoreArtifacts);
SharePointRestoreSession result = graphClient.solutions().backupRestore().sharePointRestoreSessions().post(sharePointRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointRestoreSession = {
  siteRestoreArtifacts: [
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

await client.api('/solutions/backupRestore/sharePointRestoreSessions')
	.post(sharePointRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SharePointRestoreSession;
use Microsoft\Graph\Generated\Models\SiteRestoreArtifact;
use Microsoft\Graph\Generated\Models\RestorePoint;
use Microsoft\Graph\Generated\Models\DestinationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointRestoreSession();
$siteRestoreArtifactsSiteRestoreArtifact1 = new SiteRestoreArtifact();
$siteRestoreArtifactsSiteRestoreArtifact1RestorePoint = new RestorePoint();
$siteRestoreArtifactsSiteRestoreArtifact1RestorePoint->setId('1f1fccc3-a642-4f61-bf49-f37b9a888279');
$siteRestoreArtifactsSiteRestoreArtifact1->setRestorePoint($siteRestoreArtifactsSiteRestoreArtifact1RestorePoint);
$siteRestoreArtifactsSiteRestoreArtifact1->setDestinationType(new DestinationType('inPlace'));
$siteRestoreArtifactsArray []= $siteRestoreArtifactsSiteRestoreArtifact1;
$siteRestoreArtifactsSiteRestoreArtifact2 = new SiteRestoreArtifact();
$siteRestoreArtifactsSiteRestoreArtifact2RestorePoint = new RestorePoint();
$siteRestoreArtifactsSiteRestoreArtifact2RestorePoint->setId('1f1fccc3-a642-4f61-bf49-f37b9a888280');
$siteRestoreArtifactsSiteRestoreArtifact2->setRestorePoint($siteRestoreArtifactsSiteRestoreArtifact2RestorePoint);
$siteRestoreArtifactsSiteRestoreArtifact2->setDestinationType(new DestinationType('inPlace'));
$siteRestoreArtifactsArray []= $siteRestoreArtifactsSiteRestoreArtifact2;
$requestBody->setSiteRestoreArtifacts($siteRestoreArtifactsArray);


$result = $graphServiceClient->solutions()->backupRestore()->sharePointRestoreSessions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	siteRestoreArtifacts = @(
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

New-MgSolutionBackupRestoreSharePointRestoreSession -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.share_point_restore_session import SharePointRestoreSession
from msgraph.generated.models.site_restore_artifact import SiteRestoreArtifact
from msgraph.generated.models.restore_point import RestorePoint
from msgraph.generated.models.destination_type import DestinationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointRestoreSession(
	site_restore_artifacts = [
		SiteRestoreArtifact(
			restore_point = RestorePoint(
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888279",
			),
			destination_type = DestinationType.InPlace,
		),
		SiteRestoreArtifact(
			restore_point = RestorePoint(
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888280",
			),
			destination_type = DestinationType.InPlace,
		),
	],
)

result = await graph_client.solutions.backup_restore.share_point_restore_sessions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": " /solutions/backupRestore/$metadata#restoreSessions/$entity",
  "@odata.id": "/solutions/backupRestore/sharepointRestoreSessions(61633878-8321-4950-bfaf-ed285bdd1461)",
  "@odata.type": "#microsoft.graph.sharepointRestoreSession",
  "id": "61633878-8321-4950-bfaf-ed285bdd1461",
  "status": "activating",
  "restoreJobType": "standard",
  "restoreSessionArtifactCount": {
    "total": 2,
    "completed": 0,
    "inProgress": 2,
    "failed": 0
  },
  "createdBy": {
    "application": {
      "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "displayName": "Microsoft Enhanced Restore"
    },
    "user": {
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
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "User2"
    }
  },
  "lastModifiedDateTime": "2015-06-19T12:01:03.45Z"
}
```

### Example 2: Create a granular restore session

The following example shows how to create a granular restore session.

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointRestoreSessions
Content-Type: application/json

{
  "granularSiteRestoreArtifacts": [
    {
      "browseSessionId": "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
      "id": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
    },
    {
      "browseSessionId": "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
      "id": "b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SharePointRestoreSession
{
	GranularSiteRestoreArtifacts = new List<GranularSiteRestoreArtifact>
	{
		new GranularSiteRestoreArtifact
		{
			BrowseSessionId = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
			Id = "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
		},
		new GranularSiteRestoreArtifact
		{
			BrowseSessionId = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
			Id = "b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.SharePointRestoreSessions.PostAsync(requestBody);
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

requestBody := graphmodels.NewSharePointRestoreSession()


granularSiteRestoreArtifact := graphmodels.NewGranularSiteRestoreArtifact()
browseSessionId := "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6"
granularSiteRestoreArtifact.SetBrowseSessionId(&browseSessionId) 
id := "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
granularSiteRestoreArtifact.SetId(&id) 
granularSiteRestoreArtifact1 := graphmodels.NewGranularSiteRestoreArtifact()
browseSessionId := "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6"
granularSiteRestoreArtifact1.SetBrowseSessionId(&browseSessionId) 
id := "b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
granularSiteRestoreArtifact1.SetId(&id) 

granularSiteRestoreArtifacts := []graphmodels.GranularSiteRestoreArtifactable {
	granularSiteRestoreArtifact,
	granularSiteRestoreArtifact1,
}
requestBody.SetGranularSiteRestoreArtifacts(granularSiteRestoreArtifacts)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sharePointRestoreSessions, err := graphClient.Solutions().BackupRestore().SharePointRestoreSessions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointRestoreSession sharePointRestoreSession = new SharePointRestoreSession();
LinkedList<GranularSiteRestoreArtifact> granularSiteRestoreArtifacts = new LinkedList<GranularSiteRestoreArtifact>();
GranularSiteRestoreArtifact granularSiteRestoreArtifact = new GranularSiteRestoreArtifact();
granularSiteRestoreArtifact.setBrowseSessionId("eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6");
granularSiteRestoreArtifact.setId("a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2");
granularSiteRestoreArtifacts.add(granularSiteRestoreArtifact);
GranularSiteRestoreArtifact granularSiteRestoreArtifact1 = new GranularSiteRestoreArtifact();
granularSiteRestoreArtifact1.setBrowseSessionId("eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6");
granularSiteRestoreArtifact1.setId("b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2");
granularSiteRestoreArtifacts.add(granularSiteRestoreArtifact1);
sharePointRestoreSession.setGranularSiteRestoreArtifacts(granularSiteRestoreArtifacts);
SharePointRestoreSession result = graphClient.solutions().backupRestore().sharePointRestoreSessions().post(sharePointRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointRestoreSession = {
  granularSiteRestoreArtifacts: [
    {
      browseSessionId: 'eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6',
      id: 'a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2'
    },
    {
      browseSessionId: 'eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6',
      id: 'b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2'
    }
  ]
};

await client.api('/solutions/backupRestore/sharePointRestoreSessions')
	.post(sharePointRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SharePointRestoreSession;
use Microsoft\Graph\Generated\Models\GranularSiteRestoreArtifact;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointRestoreSession();
$granularSiteRestoreArtifactsGranularSiteRestoreArtifact1 = new GranularSiteRestoreArtifact();
$granularSiteRestoreArtifactsGranularSiteRestoreArtifact1->setBrowseSessionId('eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6');
$granularSiteRestoreArtifactsGranularSiteRestoreArtifact1->setId('a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2');
$granularSiteRestoreArtifactsArray []= $granularSiteRestoreArtifactsGranularSiteRestoreArtifact1;
$granularSiteRestoreArtifactsGranularSiteRestoreArtifact2 = new GranularSiteRestoreArtifact();
$granularSiteRestoreArtifactsGranularSiteRestoreArtifact2->setBrowseSessionId('eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6');
$granularSiteRestoreArtifactsGranularSiteRestoreArtifact2->setId('b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2');
$granularSiteRestoreArtifactsArray []= $granularSiteRestoreArtifactsGranularSiteRestoreArtifact2;
$requestBody->setGranularSiteRestoreArtifacts($granularSiteRestoreArtifactsArray);


$result = $graphServiceClient->solutions()->backupRestore()->sharePointRestoreSessions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	granularSiteRestoreArtifacts = @(
		@{
			browseSessionId = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6"
			id = "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
		}
		@{
			browseSessionId = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6"
			id = "b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
		}
	)
}

New-MgSolutionBackupRestoreSharePointRestoreSession -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.share_point_restore_session import SharePointRestoreSession
from msgraph.generated.models.granular_site_restore_artifact import GranularSiteRestoreArtifact
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointRestoreSession(
	granular_site_restore_artifacts = [
		GranularSiteRestoreArtifact(
			browse_session_id = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
			id = "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
		),
		GranularSiteRestoreArtifact(
			browse_session_id = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
			id = "b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
		),
	],
)

result = await graph_client.solutions.backup_restore.share_point_restore_sessions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#restoreSessions/$entity",
  "@odata.id": "/solutions/backupRestore/sharepointRestoreSessions(61633878-8321-4950-bfaf-ed285bdd1461)",
  "@odata.type": "#microsoft.graph.sharepointRestoreSession",
  "id": "61633878-8321-4950-bfaf-ed285bdd1461",
  "status": "draft",
  "restoreJobType": "granular",
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
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "User2"
    }
  },
  "lastModifiedDateTime": "2015-06-19T12:01:03.45Z"
}
```
