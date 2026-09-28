<!-- Source: https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-post-driverestoreartifactsbulkadditionrequests?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-28 -->

# Create driveRestoreArtifactsBulkAdditionRequest

Namespace: microsoft.graph

Create a [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object associated with a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0).

The following steps describe how to create and manage a **oneDriveForBusinessRestoreSession** with bulk artifact additions.

1. Create a new [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) with empty payload.
2. Create a new [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object associated with a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0).
3. Get the status of the [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) for the OneDrive for work or school restore session. The initial status upon creation is `active` and remains in this state until the [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) is activated.
4. Activate the [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) created in the first step.
5. Monitor the status of the [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0). When all the drives are added to the corresponding [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0), the status of the [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) changes to `completed`. If any failures occur during resource resolution, the status changes to `completedWithErrors`.

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
POST /solutions/backupRestore/oneDriveForBusinessRestoreSessions/{oneDriveForBusinessRestoreSessionId}/driveRestoreArtifactsBulkAdditionRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object.

You can specify the following properties when you create a **driveRestoreArtifactsBulkAdditionRequest** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| directoryObjectIds | String collection | The list of directory object IDs. Optional. |
| drives | String collection | The list of OneDrive for work or school email addresses. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Request

The following example shows a request that adds a list of drives to the specified OneDrive for work or school restore session in a bulk operation.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions/493635f0-b8c0-4c7f-bcb7-b20c85d97efe/driveRestoreArtifactsBulkAdditionRequests
Content-Type: application/json

{
  "displayName": "ODB-BulkRestoreArtifacts",
  "drives": [
    "contoso1@micorosft.com",
    "consotos2@microsoft.com",
    "contoso3@microsoft.com"
  ],
  "directoryObjectIds": [],
  "protectionUnitIds": [],
  "protectionTimePeriod": {
    "startDateTime": "2021-01-01T00:00:00Z",
    "endDateTime": "2021-01-08T00:00:00Z"
  },
  "destinationType": "new",
  "tags": "fastRestore",
  "restorePointPreference": "latest"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new DriveRestoreArtifactsBulkAdditionRequest
{
	DisplayName = "ODB-BulkRestoreArtifacts",
	Drives = new List<string>
	{
		"contoso1@micorosft.com",
		"consotos2@microsoft.com",
		"contoso3@microsoft.com",
	},
	DirectoryObjectIds = new List<string>
	{
	},
	ProtectionUnitIds = new List<string>
	{
	},
	ProtectionTimePeriod = new TimePeriod
	{
		StartDateTime = DateTimeOffset.Parse("2021-01-01T00:00:00Z"),
		EndDateTime = DateTimeOffset.Parse("2021-01-08T00:00:00Z"),
	},
	DestinationType = DestinationType.New,
	Tags = RestorePointTags.FastRestore,
	RestorePointPreference = RestorePointPreference.Latest,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.OneDriveForBusinessRestoreSessions["{oneDriveForBusinessRestoreSession-id}"].DriveRestoreArtifactsBulkAdditionRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewDriveRestoreArtifactsBulkAdditionRequest()
displayName := "ODB-BulkRestoreArtifacts"
requestBody.SetDisplayName(&displayName) 
drives := []string {
	"contoso1@micorosft.com",
	"consotos2@microsoft.com",
	"contoso3@microsoft.com",
}
requestBody.SetDrives(drives)
directoryObjectIds := []string {

}
requestBody.SetDirectoryObjectIds(directoryObjectIds)
protectionUnitIds := []string {

}
requestBody.SetProtectionUnitIds(protectionUnitIds)
protectionTimePeriod := graphmodels.NewTimePeriod()
startDateTime , err := time.Parse(time.RFC3339, "2021-01-01T00:00:00Z")
protectionTimePeriod.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2021-01-08T00:00:00Z")
protectionTimePeriod.SetEndDateTime(&endDateTime) 
requestBody.SetProtectionTimePeriod(protectionTimePeriod)
destinationType := graphmodels.NEW_DESTINATIONTYPE 
requestBody.SetDestinationType(&destinationType) 
tags := graphmodels.FASTRESTORE_RESTOREPOINTTAGS 
requestBody.SetTags(&tags) 
restorePointPreference := graphmodels.LATEST_RESTOREPOINTPREFERENCE 
requestBody.SetRestorePointPreference(&restorePointPreference) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
driveRestoreArtifactsBulkAdditionRequests, err := graphClient.Solutions().BackupRestore().OneDriveForBusinessRestoreSessions().ByOneDriveForBusinessRestoreSessionId("oneDriveForBusinessRestoreSession-id").DriveRestoreArtifactsBulkAdditionRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DriveRestoreArtifactsBulkAdditionRequest driveRestoreArtifactsBulkAdditionRequest = new DriveRestoreArtifactsBulkAdditionRequest();
driveRestoreArtifactsBulkAdditionRequest.setDisplayName("ODB-BulkRestoreArtifacts");
LinkedList<String> drives = new LinkedList<String>();
drives.add("contoso1@micorosft.com");
drives.add("consotos2@microsoft.com");
drives.add("contoso3@microsoft.com");
driveRestoreArtifactsBulkAdditionRequest.setDrives(drives);
LinkedList<String> directoryObjectIds = new LinkedList<String>();
driveRestoreArtifactsBulkAdditionRequest.setDirectoryObjectIds(directoryObjectIds);
LinkedList<String> protectionUnitIds = new LinkedList<String>();
driveRestoreArtifactsBulkAdditionRequest.setProtectionUnitIds(protectionUnitIds);
TimePeriod protectionTimePeriod = new TimePeriod();
OffsetDateTime startDateTime = OffsetDateTime.parse("2021-01-01T00:00:00Z");
protectionTimePeriod.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2021-01-08T00:00:00Z");
protectionTimePeriod.setEndDateTime(endDateTime);
driveRestoreArtifactsBulkAdditionRequest.setProtectionTimePeriod(protectionTimePeriod);
driveRestoreArtifactsBulkAdditionRequest.setDestinationType(DestinationType.New);
driveRestoreArtifactsBulkAdditionRequest.setTags(EnumSet.of(RestorePointTags.FastRestore));
driveRestoreArtifactsBulkAdditionRequest.setRestorePointPreference(RestorePointPreference.Latest);
DriveRestoreArtifactsBulkAdditionRequest result = graphClient.solutions().backupRestore().oneDriveForBusinessRestoreSessions().byOneDriveForBusinessRestoreSessionId("{oneDriveForBusinessRestoreSession-id}").driveRestoreArtifactsBulkAdditionRequests().post(driveRestoreArtifactsBulkAdditionRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const driveRestoreArtifactsBulkAdditionRequest = {
  displayName: 'ODB-BulkRestoreArtifacts',
  drives: [
    'contoso1@micorosft.com',
    'consotos2@microsoft.com',
    'contoso3@microsoft.com'
  ],
  directoryObjectIds: [],
  protectionUnitIds: [],
  protectionTimePeriod: {
    startDateTime: '2021-01-01T00:00:00Z',
    endDateTime: '2021-01-08T00:00:00Z'
  },
  destinationType: 'new',
  tags: 'fastRestore',
  restorePointPreference: 'latest'
};

await client.api('/solutions/backupRestore/oneDriveForBusinessRestoreSessions/493635f0-b8c0-4c7f-bcb7-b20c85d97efe/driveRestoreArtifactsBulkAdditionRequests')
	.post(driveRestoreArtifactsBulkAdditionRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\DriveRestoreArtifactsBulkAdditionRequest;
use Microsoft\Graph\Generated\Models\TimePeriod;
use Microsoft\Graph\Generated\Models\DestinationType;
use Microsoft\Graph\Generated\Models\RestorePointTags;
use Microsoft\Graph\Generated\Models\RestorePointPreference;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DriveRestoreArtifactsBulkAdditionRequest();
$requestBody->setDisplayName('ODB-BulkRestoreArtifacts');
$requestBody->setDrives(['contoso1@micorosft.com', 'consotos2@microsoft.com', 'contoso3@microsoft.com', 	]);
$requestBody->setDirectoryObjectIds([	]);
$requestBody->setProtectionUnitIds([	]);
$protectionTimePeriod = new TimePeriod();
$protectionTimePeriod->setStartDateTime(new \DateTime('2021-01-01T00:00:00Z'));
$protectionTimePeriod->setEndDateTime(new \DateTime('2021-01-08T00:00:00Z'));
$requestBody->setProtectionTimePeriod($protectionTimePeriod);
$requestBody->setDestinationType(new DestinationType('new'));
$requestBody->setTags(new RestorePointTags('fastRestore'));
$requestBody->setRestorePointPreference(new RestorePointPreference('latest'));

$result = $graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessRestoreSessions()->byOneDriveForBusinessRestoreSessionId('oneDriveForBusinessRestoreSession-id')->driveRestoreArtifactsBulkAdditionRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	displayName = "ODB-BulkRestoreArtifacts"
	drives = @(
	"contoso1@micorosft.com"
"consotos2@microsoft.com"
"contoso3@microsoft.com"
)
directoryObjectIds = @(
)
protectionUnitIds = @(
)
protectionTimePeriod = @{
startDateTime = [System.DateTime]::Parse("2021-01-01T00:00:00Z")
endDateTime = [System.DateTime]::Parse("2021-01-08T00:00:00Z")
}
destinationType = "new"
tags = "fastRestore"
restorePointPreference = "latest"
}

New-MgSolutionBackupRestoreOneDriveForBusinessRestoreSessionDriveRestoreArtifactBulkAdditionRequest -OneDriveForBusinessRestoreSessionId $oneDriveForBusinessRestoreSessionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.drive_restore_artifacts_bulk_addition_request import DriveRestoreArtifactsBulkAdditionRequest
from msgraph.generated.models.time_period import TimePeriod
from msgraph.generated.models.destination_type import DestinationType
from msgraph.generated.models.restore_point_tags import RestorePointTags
from msgraph.generated.models.restore_point_preference import RestorePointPreference
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DriveRestoreArtifactsBulkAdditionRequest(
	display_name = "ODB-BulkRestoreArtifacts",
	drives = [
		"contoso1@micorosft.com",
		"consotos2@microsoft.com",
		"contoso3@microsoft.com",
	],
	directory_object_ids = [
	],
	protection_unit_ids = [
	],
	protection_time_period = TimePeriod(
		start_date_time = "2021-01-01T00:00:00Z",
		end_date_time = "2021-01-08T00:00:00Z",
	),
	destination_type = DestinationType.New,
	tags = RestorePointTags.FastRestore,
	restore_point_preference = RestorePointPreference.Latest,
)

result = await graph_client.solutions.backup_restore.one_drive_for_business_restore_sessions.by_one_drive_for_business_restore_session_id('oneDriveForBusinessRestoreSession-id').drive_restore_artifacts_bulk_addition_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#siteRestoreArtifactsBulkAdditionRequest/$entity",
  "id": "9cf59538-5289-4024-9fa4-9c6c2b39aaa6",
  "destinationType": "new",
  "tags": "fastRestore",
  "restorePointPreference": "latest",
  "displayName": "ODB-BulkRestoreArtifacts",
  "status": "active",
  "createdDateTime": "2024-12-03T13:09:46.3725247Z",
  "lastModifiedDateTime": "2024-12-03T13:09:46.3725247Z",
  "drives": [],
  "protectionTimePeriod": {
    "startDateTime": "2024-11-26T00:00:00Z",
    "endDateTime": "2024-12-03T00:00:00Z"
  },
  "createdBy": {
    "user": {
      "identity": "fb70be35-8c8e-4c8a-b55d-f8cd95c5e23a"
    }
  },
  "lastModifiedBy": {
    "user": {
      "identity": "fb70be35-8c8e-4c8a-b55d-f8cd95c5e23a"
    }
  }
}
```
