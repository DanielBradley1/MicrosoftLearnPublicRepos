<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-onedriveforbusinessrestoresessions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Create oneDriveForBusinessRestoreSession

Namespace: microsoft.graph

Create a new [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) object. To create a granular restore session, granular drive restore artifacts must be present in the payload. A request can't include both [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) and [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) in the same **create** or **update** request.

If no payload is provided when you create the restore session, the request creates an empty `standard` restore session by default.

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
POST /solutions/backupRestore/oneDriveForBusinessRestoreSessions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) object.

You can specify the following properties when you create a **oneDriveForBusinessRestoreSession**.

| Property | Type | Description |
| :--- | :--- | :--- |
| driveRestoreArtifacts | [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) collection | A collection of [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) objects. Required. |
| granularDriveRestoreArtifacts | [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) collection | A collection of [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) objects. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions
Content-Type: application/json

{
  "driveRestoreArtifacts": [
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279" },
      "destinationType": "new"
    },
    {
      "restorePoint": { "id": "1f1fccc3-a642-4f61-bf49-f37b9a888280" },
      "destinationType": "new"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OneDriveForBusinessRestoreSession
{
	DriveRestoreArtifacts = new List<DriveRestoreArtifact>
	{
		new DriveRestoreArtifact
		{
			RestorePoint = new RestorePoint
			{
				Id = "1f1fccc3-a642-4f61-bf49-f37b9a888279",
			},
			DestinationType = DestinationType.New,
		},
		new DriveRestoreArtifact
		{
			RestorePoint = new RestorePoint
			{
				Id = "1f1fccc3-a642-4f61-bf49-f37b9a888280",
			},
			DestinationType = DestinationType.New,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.OneDriveForBusinessRestoreSessions.PostAsync(requestBody);
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

requestBody := graphmodels.NewOneDriveForBusinessRestoreSession()


driveRestoreArtifact := graphmodels.NewDriveRestoreArtifact()
restorePoint := graphmodels.NewRestorePoint()
id := "1f1fccc3-a642-4f61-bf49-f37b9a888279"
restorePoint.SetId(&id) 
driveRestoreArtifact.SetRestorePoint(restorePoint)
destinationType := graphmodels.NEW_DESTINATIONTYPE 
driveRestoreArtifact.SetDestinationType(&destinationType) 
driveRestoreArtifact1 := graphmodels.NewDriveRestoreArtifact()
restorePoint := graphmodels.NewRestorePoint()
id := "1f1fccc3-a642-4f61-bf49-f37b9a888280"
restorePoint.SetId(&id) 
driveRestoreArtifact1.SetRestorePoint(restorePoint)
destinationType := graphmodels.NEW_DESTINATIONTYPE 
driveRestoreArtifact1.SetDestinationType(&destinationType) 

driveRestoreArtifacts := []graphmodels.DriveRestoreArtifactable {
	driveRestoreArtifact,
	driveRestoreArtifact1,
}
requestBody.SetDriveRestoreArtifacts(driveRestoreArtifacts)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oneDriveForBusinessRestoreSessions, err := graphClient.Solutions().BackupRestore().OneDriveForBusinessRestoreSessions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OneDriveForBusinessRestoreSession oneDriveForBusinessRestoreSession = new OneDriveForBusinessRestoreSession();
LinkedList<DriveRestoreArtifact> driveRestoreArtifacts = new LinkedList<DriveRestoreArtifact>();
DriveRestoreArtifact driveRestoreArtifact = new DriveRestoreArtifact();
RestorePoint restorePoint = new RestorePoint();
restorePoint.setId("1f1fccc3-a642-4f61-bf49-f37b9a888279");
driveRestoreArtifact.setRestorePoint(restorePoint);
driveRestoreArtifact.setDestinationType(DestinationType.New);
driveRestoreArtifacts.add(driveRestoreArtifact);
DriveRestoreArtifact driveRestoreArtifact1 = new DriveRestoreArtifact();
RestorePoint restorePoint1 = new RestorePoint();
restorePoint1.setId("1f1fccc3-a642-4f61-bf49-f37b9a888280");
driveRestoreArtifact1.setRestorePoint(restorePoint1);
driveRestoreArtifact1.setDestinationType(DestinationType.New);
driveRestoreArtifacts.add(driveRestoreArtifact1);
oneDriveForBusinessRestoreSession.setDriveRestoreArtifacts(driveRestoreArtifacts);
OneDriveForBusinessRestoreSession result = graphClient.solutions().backupRestore().oneDriveForBusinessRestoreSessions().post(oneDriveForBusinessRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oneDriveForBusinessRestoreSession = {
  driveRestoreArtifacts: [
    {
      restorePoint: { id: '1f1fccc3-a642-4f61-bf49-f37b9a888279' },
      destinationType: 'new'
    },
    {
      restorePoint: { id: '1f1fccc3-a642-4f61-bf49-f37b9a888280' },
      destinationType: 'new'
    }
  ]
};

await client.api('/solutions/backupRestore/oneDriveForBusinessRestoreSessions')
	.post(oneDriveForBusinessRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OneDriveForBusinessRestoreSession;
use Microsoft\Graph\Generated\Models\DriveRestoreArtifact;
use Microsoft\Graph\Generated\Models\RestorePoint;
use Microsoft\Graph\Generated\Models\DestinationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OneDriveForBusinessRestoreSession();
$driveRestoreArtifactsDriveRestoreArtifact1 = new DriveRestoreArtifact();
$driveRestoreArtifactsDriveRestoreArtifact1RestorePoint = new RestorePoint();
$driveRestoreArtifactsDriveRestoreArtifact1RestorePoint->setId('1f1fccc3-a642-4f61-bf49-f37b9a888279');
$driveRestoreArtifactsDriveRestoreArtifact1->setRestorePoint($driveRestoreArtifactsDriveRestoreArtifact1RestorePoint);
$driveRestoreArtifactsDriveRestoreArtifact1->setDestinationType(new DestinationType('new'));
$driveRestoreArtifactsArray []= $driveRestoreArtifactsDriveRestoreArtifact1;
$driveRestoreArtifactsDriveRestoreArtifact2 = new DriveRestoreArtifact();
$driveRestoreArtifactsDriveRestoreArtifact2RestorePoint = new RestorePoint();
$driveRestoreArtifactsDriveRestoreArtifact2RestorePoint->setId('1f1fccc3-a642-4f61-bf49-f37b9a888280');
$driveRestoreArtifactsDriveRestoreArtifact2->setRestorePoint($driveRestoreArtifactsDriveRestoreArtifact2RestorePoint);
$driveRestoreArtifactsDriveRestoreArtifact2->setDestinationType(new DestinationType('new'));
$driveRestoreArtifactsArray []= $driveRestoreArtifactsDriveRestoreArtifact2;
$requestBody->setDriveRestoreArtifacts($driveRestoreArtifactsArray);


$result = $graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessRestoreSessions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	driveRestoreArtifacts = @(
		@{
			restorePoint = @{
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888279"
			}
			destinationType = "new"
		}
		@{
			restorePoint = @{
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888280"
			}
			destinationType = "new"
		}
	)
}

New-MgSolutionBackupRestoreOneDriveForBusinessRestoreSession -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.one_drive_for_business_restore_session import OneDriveForBusinessRestoreSession
from msgraph.generated.models.drive_restore_artifact import DriveRestoreArtifact
from msgraph.generated.models.restore_point import RestorePoint
from msgraph.generated.models.destination_type import DestinationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OneDriveForBusinessRestoreSession(
	drive_restore_artifacts = [
		DriveRestoreArtifact(
			restore_point = RestorePoint(
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888279",
			),
			destination_type = DestinationType.New,
		),
		DriveRestoreArtifact(
			restore_point = RestorePoint(
				id = "1f1fccc3-a642-4f61-bf49-f37b9a888280",
			),
			destination_type = DestinationType.New,
		),
	],
)

result = await graph_client.solutions.backup_restore.one_drive_for_business_restore_sessions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#oneDriveForBusinessRestoreSession/$entity",
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
      "displayName": "User1"
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
      "displayName": "User2"
    }
  },
  "lastModifiedDateTime": "2023-03-30T12:01:03.45Z"
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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions
Content-Type: application/json

{
  "granularDriveRestoreArtifacts": [
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

var requestBody = new OneDriveForBusinessRestoreSession
{
	GranularDriveRestoreArtifacts = new List<GranularDriveRestoreArtifact>
	{
		new GranularDriveRestoreArtifact
		{
			BrowseSessionId = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
			Id = "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
		},
		new GranularDriveRestoreArtifact
		{
			BrowseSessionId = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
			Id = "b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.OneDriveForBusinessRestoreSessions.PostAsync(requestBody);
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

requestBody := graphmodels.NewOneDriveForBusinessRestoreSession()


granularDriveRestoreArtifact := graphmodels.NewGranularDriveRestoreArtifact()
browseSessionId := "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6"
granularDriveRestoreArtifact.SetBrowseSessionId(&browseSessionId) 
id := "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
granularDriveRestoreArtifact.SetId(&id) 
granularDriveRestoreArtifact1 := graphmodels.NewGranularDriveRestoreArtifact()
browseSessionId := "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6"
granularDriveRestoreArtifact1.SetBrowseSessionId(&browseSessionId) 
id := "b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
granularDriveRestoreArtifact1.SetId(&id) 

granularDriveRestoreArtifacts := []graphmodels.GranularDriveRestoreArtifactable {
	granularDriveRestoreArtifact,
	granularDriveRestoreArtifact1,
}
requestBody.SetGranularDriveRestoreArtifacts(granularDriveRestoreArtifacts)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oneDriveForBusinessRestoreSessions, err := graphClient.Solutions().BackupRestore().OneDriveForBusinessRestoreSessions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OneDriveForBusinessRestoreSession oneDriveForBusinessRestoreSession = new OneDriveForBusinessRestoreSession();
LinkedList<GranularDriveRestoreArtifact> granularDriveRestoreArtifacts = new LinkedList<GranularDriveRestoreArtifact>();
GranularDriveRestoreArtifact granularDriveRestoreArtifact = new GranularDriveRestoreArtifact();
granularDriveRestoreArtifact.setBrowseSessionId("eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6");
granularDriveRestoreArtifact.setId("a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2");
granularDriveRestoreArtifacts.add(granularDriveRestoreArtifact);
GranularDriveRestoreArtifact granularDriveRestoreArtifact1 = new GranularDriveRestoreArtifact();
granularDriveRestoreArtifact1.setBrowseSessionId("eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6");
granularDriveRestoreArtifact1.setId("b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2");
granularDriveRestoreArtifacts.add(granularDriveRestoreArtifact1);
oneDriveForBusinessRestoreSession.setGranularDriveRestoreArtifacts(granularDriveRestoreArtifacts);
OneDriveForBusinessRestoreSession result = graphClient.solutions().backupRestore().oneDriveForBusinessRestoreSessions().post(oneDriveForBusinessRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oneDriveForBusinessRestoreSession = {
  granularDriveRestoreArtifacts: [
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

await client.api('/solutions/backupRestore/oneDriveForBusinessRestoreSessions')
	.post(oneDriveForBusinessRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OneDriveForBusinessRestoreSession;
use Microsoft\Graph\Generated\Models\GranularDriveRestoreArtifact;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OneDriveForBusinessRestoreSession();
$granularDriveRestoreArtifactsGranularDriveRestoreArtifact1 = new GranularDriveRestoreArtifact();
$granularDriveRestoreArtifactsGranularDriveRestoreArtifact1->setBrowseSessionId('eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6');
$granularDriveRestoreArtifactsGranularDriveRestoreArtifact1->setId('a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2');
$granularDriveRestoreArtifactsArray []= $granularDriveRestoreArtifactsGranularDriveRestoreArtifact1;
$granularDriveRestoreArtifactsGranularDriveRestoreArtifact2 = new GranularDriveRestoreArtifact();
$granularDriveRestoreArtifactsGranularDriveRestoreArtifact2->setBrowseSessionId('eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6');
$granularDriveRestoreArtifactsGranularDriveRestoreArtifact2->setId('b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2');
$granularDriveRestoreArtifactsArray []= $granularDriveRestoreArtifactsGranularDriveRestoreArtifact2;
$requestBody->setGranularDriveRestoreArtifacts($granularDriveRestoreArtifactsArray);


$result = $graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessRestoreSessions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	granularDriveRestoreArtifacts = @(
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

New-MgSolutionBackupRestoreOneDriveForBusinessRestoreSession -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.one_drive_for_business_restore_session import OneDriveForBusinessRestoreSession
from msgraph.generated.models.granular_drive_restore_artifact import GranularDriveRestoreArtifact
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OneDriveForBusinessRestoreSession(
	granular_drive_restore_artifacts = [
		GranularDriveRestoreArtifact(
			browse_session_id = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
			id = "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
		),
		GranularDriveRestoreArtifact(
			browse_session_id = "eJxVjEEKwjAQRfc80xeIleluFd2HRkZCgAIEu9CO3aUv78W4H_q_NgQY2gSJHT8IoOhrl5AzosZGBk6",
			id = "b535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
		),
	],
)

result = await graph_client.solutions.backup_restore.one_drive_for_business_restore_sessions.post(request_body)
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
  "@odata.context": "/solutions/backupRestore/$metadata#oneDriveForBusinessRestoreSession/$entity",
  "id": "959ba739-70b5-43c4-8c90-b2c22014f18b",
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
  "createdDateTime": "2023-03-30T12:01:03.45Z",
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
  "lastModifiedDateTime": "2023-03-30T12:01:03.45Z"
}
```
