<!-- Source: https://learn.microsoft.com/en-us/graph/api/restorepoint-search?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# restorePoint: search

Namespace: microsoft.graph

Search for the [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) objects associated with a [protectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Search.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Search.Read.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/restorePoints/search
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| artifactQuery | [artifactQuery](https://learn.microsoft.com/en-us/graph/api/resources/artifactquery?view=graph-rest-1.0) | Contains an expression that specifies the criteria for search. Optional. |
| protectionUnitIds | String collection | The ID of the protection units. Required. |
| protectionTimePeriod | [timePeriod](https://learn.microsoft.com/en-us/graph/api/resources/timeperiod?view=graph-rest-1.0) | The start and end date time of the protection period. Required. |
| restorePointPreference | [restorePointPreference](https://learn.microsoft.com/en-us/graph/api/restorepoint-search?view=graph-rest-1.0#restorepointpreference-values) | Indicates which restore point to return. The possible values are `oldest`, `latest`. Optional. |
| tags | [restorePointTags](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0#restorepointtags-values) | The type of the restore point. The possible values are `None`, `FastRestore`, `UnknownFutureValue`. Optional. |

### restorePointPreference values

| Member | Description |
| :--- | :--- |
| latest | Returns the latest restore point for a given protection time period. |
| oldest | Returns the oldest restore point for a given protection time period. |

## Response

If successful, this action returns a `200 OK` response code and a [restorePointSearchResponse](https://learn.microsoft.com/en-us/graph/api/resources/restorepointsearchresponse?view=graph-rest-1.0) object in the response body.

Note

- Calls return one restore point per protection unit.
- You can include a maximum of 20 protection units in a single request, and the response isn't paginated.
- When you provide an expression for the **artifactQuery** property, you must provide only one protection unit ID in the **protectionUnitIds** property.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Search request

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/restorePoints/search
Content-Type: application/json

{
    "protectionUnitIds": ["23014d8c-71fe-4d00-a01a-31850bc5b42a", "43014d8c-71fe-4d00-a01a-31850bc5b42b", "63014d8c-71fe-4d00-a01a-31850bc5b42c", "83014d8c-71fe-4d00-a01a-31850bc5b42d"],
    "protectionTimePeriod": {
        "startDateTime": "2021-01-01T00:00:00Z",
        "endDateTime": "2021-01-08T00:00:00Z"
    },
    "restorePointPreference": "latest",
    "tags": "fastRestore"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Solutions.BackupRestore.RestorePoints.Search;
using Microsoft.Graph.Models;

var requestBody = new SearchPostRequestBody
{
	ProtectionUnitIds = new List<string>
	{
		"23014d8c-71fe-4d00-a01a-31850bc5b42a",
		"43014d8c-71fe-4d00-a01a-31850bc5b42b",
		"63014d8c-71fe-4d00-a01a-31850bc5b42c",
		"83014d8c-71fe-4d00-a01a-31850bc5b42d",
	},
	ProtectionTimePeriod = new TimePeriod
	{
		StartDateTime = DateTimeOffset.Parse("2021-01-01T00:00:00Z"),
		EndDateTime = DateTimeOffset.Parse("2021-01-08T00:00:00Z"),
	},
	RestorePointPreference = RestorePointPreference.Latest,
	Tags = RestorePointTags.FastRestore,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.RestorePoints.Search.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsolutions "github.com/microsoftgraph/msgraph-sdk-go/solutions"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphsolutions.NewSearchPostRequestBody()
protectionUnitIds := []string {
	"23014d8c-71fe-4d00-a01a-31850bc5b42a",
	"43014d8c-71fe-4d00-a01a-31850bc5b42b",
	"63014d8c-71fe-4d00-a01a-31850bc5b42c",
	"83014d8c-71fe-4d00-a01a-31850bc5b42d",
}
requestBody.SetProtectionUnitIds(protectionUnitIds)
protectionTimePeriod := graphmodels.NewTimePeriod()
startDateTime , err := time.Parse(time.RFC3339, "2021-01-01T00:00:00Z")
protectionTimePeriod.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2021-01-08T00:00:00Z")
protectionTimePeriod.SetEndDateTime(&endDateTime) 
requestBody.SetProtectionTimePeriod(protectionTimePeriod)
restorePointPreference := graphmodels.LATEST_RESTOREPOINTPREFERENCE 
requestBody.SetRestorePointPreference(&restorePointPreference) 
tags := graphmodels.FASTRESTORE_RESTOREPOINTTAGS 
requestBody.SetTags(&tags) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
search, err := graphClient.Solutions().BackupRestore().RestorePoints().Search().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.solutions.backuprestore.restorepoints.search.SearchPostRequestBody searchPostRequestBody = new com.microsoft.graph.solutions.backuprestore.restorepoints.search.SearchPostRequestBody();
LinkedList<String> protectionUnitIds = new LinkedList<String>();
protectionUnitIds.add("23014d8c-71fe-4d00-a01a-31850bc5b42a");
protectionUnitIds.add("43014d8c-71fe-4d00-a01a-31850bc5b42b");
protectionUnitIds.add("63014d8c-71fe-4d00-a01a-31850bc5b42c");
protectionUnitIds.add("83014d8c-71fe-4d00-a01a-31850bc5b42d");
searchPostRequestBody.setProtectionUnitIds(protectionUnitIds);
TimePeriod protectionTimePeriod = new TimePeriod();
OffsetDateTime startDateTime = OffsetDateTime.parse("2021-01-01T00:00:00Z");
protectionTimePeriod.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2021-01-08T00:00:00Z");
protectionTimePeriod.setEndDateTime(endDateTime);
searchPostRequestBody.setProtectionTimePeriod(protectionTimePeriod);
searchPostRequestBody.setRestorePointPreference(RestorePointPreference.Latest);
searchPostRequestBody.setTags(EnumSet.of(RestorePointTags.FastRestore));
var result = graphClient.solutions().backupRestore().restorePoints().search().post(searchPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const restorePointSearchResponse = {
    protectionUnitIds: ['23014d8c-71fe-4d00-a01a-31850bc5b42a', '43014d8c-71fe-4d00-a01a-31850bc5b42b', '63014d8c-71fe-4d00-a01a-31850bc5b42c', '83014d8c-71fe-4d00-a01a-31850bc5b42d'],
    protectionTimePeriod: {
        startDateTime: '2021-01-01T00:00:00Z',
        endDateTime: '2021-01-08T00:00:00Z'
    },
    restorePointPreference: 'latest',
    tags: 'fastRestore'
};

await client.api('/solutions/backupRestore/restorePoints/search')
	.post(restorePointSearchResponse);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Solutions\BackupRestore\RestorePoints\Search\SearchPostRequestBody;
use Microsoft\Graph\Generated\Models\TimePeriod;
use Microsoft\Graph\Generated\Models\RestorePointPreference;
use Microsoft\Graph\Generated\Models\RestorePointTags;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SearchPostRequestBody();
$requestBody->setProtectionUnitIds(['23014d8c-71fe-4d00-a01a-31850bc5b42a', '43014d8c-71fe-4d00-a01a-31850bc5b42b', '63014d8c-71fe-4d00-a01a-31850bc5b42c', '83014d8c-71fe-4d00-a01a-31850bc5b42d', 	]);
$protectionTimePeriod = new TimePeriod();
$protectionTimePeriod->setStartDateTime(new \DateTime('2021-01-01T00:00:00Z'));
$protectionTimePeriod->setEndDateTime(new \DateTime('2021-01-08T00:00:00Z'));
$requestBody->setProtectionTimePeriod($protectionTimePeriod);
$requestBody->setRestorePointPreference(new RestorePointPreference('latest'));
$requestBody->setTags(new RestorePointTags('fastRestore'));

$result = $graphServiceClient->solutions()->backupRestore()->restorePoints()->search()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	protectionUnitIds = @(
	"23014d8c-71fe-4d00-a01a-31850bc5b42a"
"43014d8c-71fe-4d00-a01a-31850bc5b42b"
"63014d8c-71fe-4d00-a01a-31850bc5b42c"
"83014d8c-71fe-4d00-a01a-31850bc5b42d"
)
protectionTimePeriod = @{
startDateTime = [System.DateTime]::Parse("2021-01-01T00:00:00Z")
endDateTime = [System.DateTime]::Parse("2021-01-08T00:00:00Z")
}
restorePointPreference = "latest"
tags = "fastRestore"
}

Search-MgSolutionBackupRestorePoint -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.solutions.backuprestore.restorepoints.search.search_post_request_body import SearchPostRequestBody
from msgraph.generated.models.time_period import TimePeriod
from msgraph.generated.models.restore_point_preference import RestorePointPreference
from msgraph.generated.models.restore_point_tags import RestorePointTags
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SearchPostRequestBody(
	protection_unit_ids = [
		"23014d8c-71fe-4d00-a01a-31850bc5b42a",
		"43014d8c-71fe-4d00-a01a-31850bc5b42b",
		"63014d8c-71fe-4d00-a01a-31850bc5b42c",
		"83014d8c-71fe-4d00-a01a-31850bc5b42d",
	],
	protection_time_period = TimePeriod(
		start_date_time = "2021-01-01T00:00:00Z",
		end_date_time = "2021-01-08T00:00:00Z",
	),
	restore_point_preference = RestorePointPreference.Latest,
	tags = RestorePointTags.FastRestore,
)

result = await graph_client.solutions.backup_restore.restore_points.search.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

- Calls return a maximum of five restore points.
- You can include a maximum of 20 protection units in a single request, and the response isn't paginated.

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context":"/solutions/backupRestore/$metadata#restorePoints",
    "searchResponseId": "M2UyZDAwMDAwMDMxMzkzYTMyNj",
    "searchResults": [
        {
            "restorePoint": {
                "@odata.type": "#microsoft.graph.restorePoint",
                "id":"1f1fccc3-a642-4f61-bf49-f37b9a888279",
                "protectionDateTime":"2023-01-04T00:00:00Z",
                "expirationDateTime":"2024-01-04T00:00:00Z",
                "protectionUnit":{
                   "@odata.type": "#microsoft.graph.siteProtectionUnit",
                   "id":"23014d8c-71fe-4d00-a01a-31850bc5b42a",
                   "siteId":"344d9337-d8f0-456e-92cd-00a3abdd2093",
                   "policyId":"9fec8e78-bce4-4aaf-ab1b-5451cc387264"
               },
               "tags": "fastRestore"
            }
        },
        {
            "restorePoint": {
                "@odata.type": "#microsoft.graph.restorePoint",
                "id":"cdf4a823-sfde-ki2s-kmsj-clu2nsdk43ga",
                "protectionDateTime":"2023-01-03T00:00:00Z",
                "expirationDateTime":"2024-01-03T00:00:00Z",
                "protectionUnit":{
                   "@odata.type": "#microsoft.graph.siteProtectionUnit",
                   "id":"43014d8c-71fe-4d00-a01a-31850bc5b42b",
                   "siteId":"344d9337-d8f0-456e-92cd-00a3abdd2093",
                   "policyId":"9fec8e78-bce4-4aaf-ab1b-5451cc387264"
               },
               "tags": "fastRestore"
            }
        },
        {
            "restorePoint": {
                "@odata.type": "#microsoft.graph.restorePoint",
                "id":"1f1fccc3-a642-4f61-bf49-f37b9a888280",
                "protectionDateTime":"2023-01-02T00:00:00Z",
                "expirationDateTime":"2024-01-02T00:00:00Z",
                "protectionUnit":{
                   "@odata.type": "#microsoft.graph.siteProtectionUnit",
                   "id":"83014d8c-71fe-4d00-a01a-31850bc5b42c",
                   "siteId":"344d9337-d8f0-456e-92cd-00a3abdd2093",
                   "policyId":"9fec8e78-bce4-4aaf-ab1b-5451cc387264"
                },
                "tags": "fastRestore"
            }
        }
    ],
    "noResultProtectionUnitIds": ["63014d8c-71fe-4d00-a01a-31850bc5b42c"]
}
```

### Example 2: Search with artifactQuery expression

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/restorePoints/search
Content-Type: application/json

{
  "artifactQuery": {
    "queryExpression": "(Sender -eq 'abc@contoso.com') -and (Subject -like '*Check email*' -or Subject -like ' Important') -and (HasAttachment -eq 'true') -and (PitrDumpsterActionTriggeredTime -gt '{2024-09-21T08:20:00.0000000Z}')",
    "artifactType": "message"
  },
  "protectionUnitIds": ["23014d8c-71fe-4d00-a01a-31850bc5b42a"],
  "protectionTimePeriod": {
    "startDateTime": "2021-01-01T00:00:00Z"
  },
  "restorePointPreference": "oldest"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Solutions.BackupRestore.RestorePoints.Search;
using Microsoft.Graph.Models;

var requestBody = new SearchPostRequestBody
{
	ArtifactQuery = new ArtifactQuery
	{
		QueryExpression = "(Sender -eq 'abc@contoso.com') -and (Subject -like '*Check email*' -or Subject -like ' Important') -and (HasAttachment -eq 'true') -and (PitrDumpsterActionTriggeredTime -gt '{2024-09-21T08:20:00.0000000Z}')",
		ArtifactType = RestorableArtifact.Message,
	},
	ProtectionUnitIds = new List<string>
	{
		"23014d8c-71fe-4d00-a01a-31850bc5b42a",
	},
	ProtectionTimePeriod = new TimePeriod
	{
		StartDateTime = DateTimeOffset.Parse("2021-01-01T00:00:00Z"),
	},
	RestorePointPreference = RestorePointPreference.Oldest,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.RestorePoints.Search.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsolutions "github.com/microsoftgraph/msgraph-sdk-go/solutions"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphsolutions.NewSearchPostRequestBody()
artifactQuery := graphmodels.NewArtifactQuery()
queryExpression := "(Sender -eq 'abc@contoso.com') -and (Subject -like '*Check email*' -or Subject -like ' Important') -and (HasAttachment -eq 'true') -and (PitrDumpsterActionTriggeredTime -gt '{2024-09-21T08:20:00.0000000Z}')"
artifactQuery.SetQueryExpression(&queryExpression) 
artifactType := graphmodels.MESSAGE_RESTORABLEARTIFACT 
artifactQuery.SetArtifactType(&artifactType) 
requestBody.SetArtifactQuery(artifactQuery)
protectionUnitIds := []string {
	"23014d8c-71fe-4d00-a01a-31850bc5b42a",
}
requestBody.SetProtectionUnitIds(protectionUnitIds)
protectionTimePeriod := graphmodels.NewTimePeriod()
startDateTime , err := time.Parse(time.RFC3339, "2021-01-01T00:00:00Z")
protectionTimePeriod.SetStartDateTime(&startDateTime) 
requestBody.SetProtectionTimePeriod(protectionTimePeriod)
restorePointPreference := graphmodels.OLDEST_RESTOREPOINTPREFERENCE 
requestBody.SetRestorePointPreference(&restorePointPreference) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
search, err := graphClient.Solutions().BackupRestore().RestorePoints().Search().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.solutions.backuprestore.restorepoints.search.SearchPostRequestBody searchPostRequestBody = new com.microsoft.graph.solutions.backuprestore.restorepoints.search.SearchPostRequestBody();
ArtifactQuery artifactQuery = new ArtifactQuery();
artifactQuery.setQueryExpression("(Sender -eq 'abc@contoso.com') -and (Subject -like '*Check email*' -or Subject -like ' Important') -and (HasAttachment -eq 'true') -and (PitrDumpsterActionTriggeredTime -gt '{2024-09-21T08:20:00.0000000Z}')");
artifactQuery.setArtifactType(RestorableArtifact.Message);
searchPostRequestBody.setArtifactQuery(artifactQuery);
LinkedList<String> protectionUnitIds = new LinkedList<String>();
protectionUnitIds.add("23014d8c-71fe-4d00-a01a-31850bc5b42a");
searchPostRequestBody.setProtectionUnitIds(protectionUnitIds);
TimePeriod protectionTimePeriod = new TimePeriod();
OffsetDateTime startDateTime = OffsetDateTime.parse("2021-01-01T00:00:00Z");
protectionTimePeriod.setStartDateTime(startDateTime);
searchPostRequestBody.setProtectionTimePeriod(protectionTimePeriod);
searchPostRequestBody.setRestorePointPreference(RestorePointPreference.Oldest);
var result = graphClient.solutions().backupRestore().restorePoints().search().post(searchPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const restorePointSearchResponse = {
  artifactQuery: {
    queryExpression: '(Sender -eq \'abc@contoso.com\') -and (Subject -like \'*Check email*\' -or Subject -like \' Important\') -and (HasAttachment -eq \'true\') -and (PitrDumpsterActionTriggeredTime -gt \'{2024-09-21T08:20:00.0000000Z}\')',
    artifactType: 'message'
  },
  protectionUnitIds: ['23014d8c-71fe-4d00-a01a-31850bc5b42a'],
  protectionTimePeriod: {
    startDateTime: '2021-01-01T00:00:00Z'
  },
  restorePointPreference: 'oldest'
};

await client.api('/solutions/backupRestore/restorePoints/search')
	.post(restorePointSearchResponse);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Solutions\BackupRestore\RestorePoints\Search\SearchPostRequestBody;
use Microsoft\Graph\Generated\Models\ArtifactQuery;
use Microsoft\Graph\Generated\Models\RestorableArtifact;
use Microsoft\Graph\Generated\Models\TimePeriod;
use Microsoft\Graph\Generated\Models\RestorePointPreference;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SearchPostRequestBody();
$artifactQuery = new ArtifactQuery();
$artifactQuery->setQueryExpression('(Sender -eq \'abc@contoso.com\') -and (Subject -like \'*Check email*\' -or Subject -like \' Important\') -and (HasAttachment -eq \'true\') -and (PitrDumpsterActionTriggeredTime -gt \'{2024-09-21T08:20:00.0000000Z}\')');
$artifactQuery->setArtifactType(new RestorableArtifact('message'));
$requestBody->setArtifactQuery($artifactQuery);
$requestBody->setProtectionUnitIds(['23014d8c-71fe-4d00-a01a-31850bc5b42a', 	]);
$protectionTimePeriod = new TimePeriod();
$protectionTimePeriod->setStartDateTime(new \DateTime('2021-01-01T00:00:00Z'));
$requestBody->setProtectionTimePeriod($protectionTimePeriod);
$requestBody->setRestorePointPreference(new RestorePointPreference('oldest'));

$result = $graphServiceClient->solutions()->backupRestore()->restorePoints()->search()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	artifactQuery = @{
		queryExpression = "(Sender -eq 'abc@contoso.com') -and (Subject -like '*Check email*' -or Subject -like ' Important') -and (HasAttachment -eq 'true') -and (PitrDumpsterActionTriggeredTime -gt '{2024-09-21T08:20:00.0000000Z}')"
		artifactType = "message"
	}
	protectionUnitIds = @(
	"23014d8c-71fe-4d00-a01a-31850bc5b42a"
)
protectionTimePeriod = @{
	startDateTime = [System.DateTime]::Parse("2021-01-01T00:00:00Z")
}
restorePointPreference = "oldest"
}

Search-MgSolutionBackupRestorePoint -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.solutions.backuprestore.restorepoints.search.search_post_request_body import SearchPostRequestBody
from msgraph.generated.models.artifact_query import ArtifactQuery
from msgraph.generated.models.restorable_artifact import RestorableArtifact
from msgraph.generated.models.time_period import TimePeriod
from msgraph.generated.models.restore_point_preference import RestorePointPreference
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SearchPostRequestBody(
	artifact_query = ArtifactQuery(
		query_expression = "(Sender -eq 'abc@contoso.com') -and (Subject -like '*Check email*' -or Subject -like ' Important') -and (HasAttachment -eq 'true') -and (PitrDumpsterActionTriggeredTime -gt '{2024-09-21T08:20:00.0000000Z}')",
		artifact_type = RestorableArtifact.Message,
	),
	protection_unit_ids = [
		"23014d8c-71fe-4d00-a01a-31850bc5b42a",
	],
	protection_time_period = TimePeriod(
		start_date_time = "2021-01-01T00:00:00Z",
	),
	restore_point_preference = RestorePointPreference.Oldest,
)

result = await graph_client.solutions.backup_restore.restore_points.search.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#restorePoints",
  "searchResponseId": "M2UyZDAwMDAwMDMxMzkzYTMyNj",
  "searchResults": [
    {
      "artifactHitCount": 26,
      "restorePoint": {
        "@odata.type": "#microsoft.graph.restorePoint",
        "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279",
        "protectionDateTime": "2023-01-04T00:00:00Z",
        "expirationDateTime": "2024-01-04T00:00:00Z",
        "protectionUnit": {
          "@odata.type": "#microsoft.graph.siteProtectionUnit",
          "id": "23014d8c-71fe-4d00-a01a-31850bc5b42a",
          "siteId": "344d9337-d8f0-456e-92cd-00a3abdd2093",
          "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264"
        },
        "tags": "fastRestore"
      }
    }
  ]
}
```
