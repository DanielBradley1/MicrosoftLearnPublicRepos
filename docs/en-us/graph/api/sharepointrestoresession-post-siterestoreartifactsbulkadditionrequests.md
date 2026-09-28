<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointrestoresession-post-siterestoreartifactsbulkadditionrequests?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-28 -->

# Create siteRestoreArtifactsBulkAdditionRequests

Namespace: microsoft.graph

Create a new [siteRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object associated with a [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0).

The following steps describe how to create and manage a **sharePointRestoreSession** with bulk artifact additions:

1. Create a new [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0) with empty payload.
2. Create a new [siteRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object associated with a [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0).
3. Get the status of the [siteRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifactsbulkadditionrequest?view=graph-rest-1.0) for the SharePoint restore session. The initial status upon creation is `active` and remains in this state until the [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0) is activated.
4. Activate the [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0) created in the first step.
5. Monitor the status of the [siteRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifactsbulkadditionrequest?view=graph-rest-1.0). When all the sites are added to the corresponding [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0), the status of the [siteRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifactsbulkadditionrequest?view=graph-rest-1.0) changes to `completed`. If any failures occur during resource resolution, the status changes to `completedWithErrors`.

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
POST /solutions/backupRestore/sharePointRestoreSessions/{sharePointRestoreSessionId}/siteRestoreArtifactsBulkAdditionRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [siteRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object.

You can specify the following properties when you create a **siteRestoreArtifactsBulkAdditionRequest** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| siteIds | String collection | The list of SharePoint site IDs. Optional. |
| siteWebUrls | String collection | The list of SharePoint site URLs. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [siteRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Request

The following example shows a request that adds a list of sites to the specified SharePoint restore session in a bulk operation.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointRestoreSessions/959ba739-70b5-43c4-8c90-b2c22014f18b/siteRestoreArtifactsBulkAdditionRequests
Content-Type: application/json

{
  "displayName": "SPO-BulkRestoreArtifacts",
  "siteWebUrls": [
    "https: //contoso1.sharepoint.com",
    "https: //contoso2.sharepoint.com",
    "https: //contoso3.sharepoint.com"
  ],
  "protectionTimePeriod": {
    "startDateTime": "2024-01-01T00:00:00Z",
    "endDateTime": "2024-01-08T00:00:00Z"
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

var requestBody = new SiteRestoreArtifactsBulkAdditionRequest
{
	DisplayName = "SPO-BulkRestoreArtifacts",
	SiteWebUrls = new List<string>
	{
		"https: //contoso1.sharepoint.com",
		"https: //contoso2.sharepoint.com",
		"https: //contoso3.sharepoint.com",
	},
	ProtectionTimePeriod = new TimePeriod
	{
		StartDateTime = DateTimeOffset.Parse("2024-01-01T00:00:00Z"),
		EndDateTime = DateTimeOffset.Parse("2024-01-08T00:00:00Z"),
	},
	DestinationType = DestinationType.New,
	Tags = RestorePointTags.FastRestore,
	RestorePointPreference = RestorePointPreference.Latest,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.SharePointRestoreSessions["{sharePointRestoreSession-id}"].SiteRestoreArtifactsBulkAdditionRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewSiteRestoreArtifactsBulkAdditionRequest()
displayName := "SPO-BulkRestoreArtifacts"
requestBody.SetDisplayName(&displayName) 
siteWebUrls := []string {
	"https: //contoso1.sharepoint.com",
	"https: //contoso2.sharepoint.com",
	"https: //contoso3.sharepoint.com",
}
requestBody.SetSiteWebUrls(siteWebUrls)
protectionTimePeriod := graphmodels.NewTimePeriod()
startDateTime , err := time.Parse(time.RFC3339, "2024-01-01T00:00:00Z")
protectionTimePeriod.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2024-01-08T00:00:00Z")
protectionTimePeriod.SetEndDateTime(&endDateTime) 
requestBody.SetProtectionTimePeriod(protectionTimePeriod)
destinationType := graphmodels.NEW_DESTINATIONTYPE 
requestBody.SetDestinationType(&destinationType) 
tags := graphmodels.FASTRESTORE_RESTOREPOINTTAGS 
requestBody.SetTags(&tags) 
restorePointPreference := graphmodels.LATEST_RESTOREPOINTPREFERENCE 
requestBody.SetRestorePointPreference(&restorePointPreference) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
siteRestoreArtifactsBulkAdditionRequests, err := graphClient.Solutions().BackupRestore().SharePointRestoreSessions().BySharePointRestoreSessionId("sharePointRestoreSession-id").SiteRestoreArtifactsBulkAdditionRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SiteRestoreArtifactsBulkAdditionRequest siteRestoreArtifactsBulkAdditionRequest = new SiteRestoreArtifactsBulkAdditionRequest();
siteRestoreArtifactsBulkAdditionRequest.setDisplayName("SPO-BulkRestoreArtifacts");
LinkedList<String> siteWebUrls = new LinkedList<String>();
siteWebUrls.add("https: //contoso1.sharepoint.com");
siteWebUrls.add("https: //contoso2.sharepoint.com");
siteWebUrls.add("https: //contoso3.sharepoint.com");
siteRestoreArtifactsBulkAdditionRequest.setSiteWebUrls(siteWebUrls);
TimePeriod protectionTimePeriod = new TimePeriod();
OffsetDateTime startDateTime = OffsetDateTime.parse("2024-01-01T00:00:00Z");
protectionTimePeriod.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-01-08T00:00:00Z");
protectionTimePeriod.setEndDateTime(endDateTime);
siteRestoreArtifactsBulkAdditionRequest.setProtectionTimePeriod(protectionTimePeriod);
siteRestoreArtifactsBulkAdditionRequest.setDestinationType(DestinationType.New);
siteRestoreArtifactsBulkAdditionRequest.setTags(EnumSet.of(RestorePointTags.FastRestore));
siteRestoreArtifactsBulkAdditionRequest.setRestorePointPreference(RestorePointPreference.Latest);
SiteRestoreArtifactsBulkAdditionRequest result = graphClient.solutions().backupRestore().sharePointRestoreSessions().bySharePointRestoreSessionId("{sharePointRestoreSession-id}").siteRestoreArtifactsBulkAdditionRequests().post(siteRestoreArtifactsBulkAdditionRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const siteRestoreArtifactsBulkAdditionRequest = {
  displayName: 'SPO-BulkRestoreArtifacts',
  siteWebUrls: [
    'https: //contoso1.sharepoint.com',
    'https: //contoso2.sharepoint.com',
    'https: //contoso3.sharepoint.com'
  ],
  protectionTimePeriod: {
    startDateTime: '2024-01-01T00:00:00Z',
    endDateTime: '2024-01-08T00:00:00Z'
  },
  destinationType: 'new',
  tags: 'fastRestore',
  restorePointPreference: 'latest'
};

await client.api('/solutions/backupRestore/sharePointRestoreSessions/959ba739-70b5-43c4-8c90-b2c22014f18b/siteRestoreArtifactsBulkAdditionRequests')
	.post(siteRestoreArtifactsBulkAdditionRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SiteRestoreArtifactsBulkAdditionRequest;
use Microsoft\Graph\Generated\Models\TimePeriod;
use Microsoft\Graph\Generated\Models\DestinationType;
use Microsoft\Graph\Generated\Models\RestorePointTags;
use Microsoft\Graph\Generated\Models\RestorePointPreference;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SiteRestoreArtifactsBulkAdditionRequest();
$requestBody->setDisplayName('SPO-BulkRestoreArtifacts');
$requestBody->setSiteWebUrls(['https: //contoso1.sharepoint.com', 'https: //contoso2.sharepoint.com', 'https: //contoso3.sharepoint.com', 	]);
$protectionTimePeriod = new TimePeriod();
$protectionTimePeriod->setStartDateTime(new \DateTime('2024-01-01T00:00:00Z'));
$protectionTimePeriod->setEndDateTime(new \DateTime('2024-01-08T00:00:00Z'));
$requestBody->setProtectionTimePeriod($protectionTimePeriod);
$requestBody->setDestinationType(new DestinationType('new'));
$requestBody->setTags(new RestorePointTags('fastRestore'));
$requestBody->setRestorePointPreference(new RestorePointPreference('latest'));

$result = $graphServiceClient->solutions()->backupRestore()->sharePointRestoreSessions()->bySharePointRestoreSessionId('sharePointRestoreSession-id')->siteRestoreArtifactsBulkAdditionRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	displayName = "SPO-BulkRestoreArtifacts"
	siteWebUrls = @(
	"https: //contoso1.sharepoint.com"
"https: //contoso2.sharepoint.com"
"https: //contoso3.sharepoint.com"
)
protectionTimePeriod = @{
startDateTime = [System.DateTime]::Parse("2024-01-01T00:00:00Z")
endDateTime = [System.DateTime]::Parse("2024-01-08T00:00:00Z")
}
destinationType = "new"
tags = "fastRestore"
restorePointPreference = "latest"
}

New-MgSolutionBackupRestoreSharePointRestoreSessionSiteRestoreArtifactBulkAdditionRequest -SharePointRestoreSessionId $sharePointRestoreSessionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.site_restore_artifacts_bulk_addition_request import SiteRestoreArtifactsBulkAdditionRequest
from msgraph.generated.models.time_period import TimePeriod
from msgraph.generated.models.destination_type import DestinationType
from msgraph.generated.models.restore_point_tags import RestorePointTags
from msgraph.generated.models.restore_point_preference import RestorePointPreference
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SiteRestoreArtifactsBulkAdditionRequest(
	display_name = "SPO-BulkRestoreArtifacts",
	site_web_urls = [
		"https: //contoso1.sharepoint.com",
		"https: //contoso2.sharepoint.com",
		"https: //contoso3.sharepoint.com",
	],
	protection_time_period = TimePeriod(
		start_date_time = "2024-01-01T00:00:00Z",
		end_date_time = "2024-01-08T00:00:00Z",
	),
	destination_type = DestinationType.New,
	tags = RestorePointTags.FastRestore,
	restore_point_preference = RestorePointPreference.Latest,
)

result = await graph_client.solutions.backup_restore.share_point_restore_sessions.by_share_point_restore_session_id('sharePointRestoreSession-id').site_restore_artifacts_bulk_addition_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#siteRestoreArtifactsBulkAdditionRequest/$entity",
  "id": "4437afcf-e520-463c-90a7-ca96401d8039",
  "destinationType": "new",
  "tags": "fastRestore",
  "restorePointPreference": "latest",
  "displayName": "SPO-BulkRestoreArtifacts",
  "status": "active",
  "createdDateTime": "2024-12-03T07:47:57.6011358Z",
  "lastModifiedDateTime": "2024-12-03T07:47:57.6011358Z",
  "siteWebUrls": [],
  "protectionTimePeriod": {
    "startDateTime": "2024-01-01T00:00:00Z",
    "endDateTime": "2024-01-08T00:00:00Z"
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
