<!-- Source: https://learn.microsoft.com/en-us/graph/api/subjectrightsrequest-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# Create subjectRightsRequest

Namespace: microsoft.graph

Create a new [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SubjectRightsRequest.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

Caution

The subject rights request API under the `/privacy` node is deprecated and will stop returning data on March 30, 2025. Please use the new path under `/security`.

```http
POST /security/subjectRightsRequests
POST /privacy/subjectRightsRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| approvers | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | Collection of users who can approve the request. Currently only supported for requests of **type** `delete`. |
| collaborators | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | Collection of users who can collaborate on the request. |
| contentQuery | String | KQL based content query that should be used for search. This property is defined only for APIs accessed using the `\\security` query path and not the `\\privacy` query path. |
| dataSubject | [dataSubject](https://learn.microsoft.com/en-us/graph/api/resources/datasubject?view=graph-rest-1.0) | Contains the properties for data subject for the request. |
| dataSubjectType | dataSubjectType | Data subject type. The possible values are: `customer`, `currentEmployee`, `formerEmployee`, `prospectiveEmployee`, `student`, `teacher`, `faculty`, `other`, `unknownFutureValue`. |
| description | String | Description for the request. |
| displayName | String | Name of the request. |
| externalId | String | The external ID for the request that is immutable after creation and is used for tracking the request for the external system. This property is defined only for APIs accessed using the `\\security` query path and not the `\\privacy` query path. |
| includeAllVersions | Boolean | Include all versions of the documents. By default, the current copies of the documents are returned. If SharePoint sites have versioning enabled, including all versions automatically includes the historical copies of the documents. This property is defined only for APIs accessed using the `\\security` query path and not the `\\privacy` query path. |
| includeAuthoredContent | Boolean | Include content authored by the data subject. This property is defined only for APIs accessed using the `\\security` query path and not the `\\privacy` query path. |
| internalDueDateTime | DateTimeOffset | Internal due date that is used for tracking the request completion. |
| mailboxLocations | [subjectRightsRequestMailboxLocation](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequestmailboxlocation?view=graph-rest-1.0) | The mailbox locations that should be searched. This property is defined only for APIs accessed using the `\\security` query path and not the `\\privacy` query path. |
| pauseAfterEstimate | Boolean | Pause the request after estimate has finished. By default, the data estimate runs and then pauses, allowing you to preview results and then select the option to retrieve data in the UI. You can set this property to `false` if you want it to perform the estimate and then automatically begin with the retrieval of the content. This property is defined only for APIs accessed using the `\\security` query path and not the `\\privacy` query path. |
| regulations | String collection | One or more regulations for the request. |
| siteLocations | [subjectRightsRequestSiteLocation](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequestsitelocation?view=graph-rest-1.0) | The SharePoint and OneDrive site locations that should be searched. This property is defined only for APIs accessed using the `\\security` query path and not the `\\privacy` query path. |
| type | subjectRightsRequestType | Type of the request. The possible values are: `export`, `access`, `delete`, `tagForAction`, `unknownFutureValue`. |

## Response

If successful, this method returns a `201 Created` response code and a [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/privacy/subjectRightsRequests
Content-Type: application/json

{
  "type": "export",
  "contentQuery": "((\"Diego Siciliani\" OR \"Diego.Siciliani@contoso.com\") OR (participants:\"Diego.Siciliani@contoso.com\"))",
  "dataSubjectType": "customer",
  "externalId": "F53BF2DA-607D-412A-B568-FAA0F023AC0B",
  "displayName": "Export report for customer Id: 12345",
  "description": "This is a export request",
  "includeAllVersions": false,
  "includeAuthoredContent": true,
  "internalDueDateTime": "2022-07-20T22:42:28Z",
  "dataSubject": {
    "firstName": "Diego",
    "lastName": "Siciliani",
    "email": "Diego.Siciliani@contoso.com",
    "residency": "USA"
  },
  "mailboxLocations": null,
  "pauseAfterEstimate": true,
  "regulations": [
    "CCPA"
  ],
  "siteLocations": {
    "@odata.type": "microsoft.graph.subjectRightsRequestAllSiteLocation"
  },
  "approvers": [
    {
      "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SubjectRightsRequest
{
	Type = SubjectRightsRequestType.Export,
	ContentQuery = "((\"Diego Siciliani\" OR \"Diego.Siciliani@contoso.com\") OR (participants:\"Diego.Siciliani@contoso.com\"))",
	DataSubjectType = DataSubjectType.Customer,
	ExternalId = "F53BF2DA-607D-412A-B568-FAA0F023AC0B",
	DisplayName = "Export report for customer Id: 12345",
	Description = "This is a export request",
	IncludeAllVersions = false,
	IncludeAuthoredContent = true,
	InternalDueDateTime = DateTimeOffset.Parse("2022-07-20T22:42:28Z"),
	DataSubject = new DataSubject
	{
		FirstName = "Diego",
		LastName = "Siciliani",
		Email = "Diego.Siciliani@contoso.com",
		Residency = "USA",
	},
	MailboxLocations = null,
	PauseAfterEstimate = true,
	Regulations = new List<string>
	{
		"CCPA",
	},
	SiteLocations = new SubjectRightsRequestAllSiteLocation
	{
		OdataType = "microsoft.graph.subjectRightsRequestAllSiteLocation",
	},
	Approvers = new List<User>
	{
		new User
		{
			Id = "1B761ED2-AA7E-4D82-9CF5-C09D737B6167",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Privacy.SubjectRightsRequests.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSubjectRightsRequest()
type := graphmodels.EXPORT_SUBJECTRIGHTSREQUESTTYPE 
requestBody.SetType(&type) 
contentQuery := "((\"Diego Siciliani\" OR \"Diego.Siciliani@contoso.com\") OR (participants:\"Diego.Siciliani@contoso.com\"))"
requestBody.SetContentQuery(&contentQuery) 
dataSubjectType := graphmodels.CUSTOMER_DATASUBJECTTYPE 
requestBody.SetDataSubjectType(&dataSubjectType) 
externalId := "F53BF2DA-607D-412A-B568-FAA0F023AC0B"
requestBody.SetExternalId(&externalId) 
displayName := "Export report for customer Id: 12345"
requestBody.SetDisplayName(&displayName) 
description := "This is a export request"
requestBody.SetDescription(&description) 
includeAllVersions := false
requestBody.SetIncludeAllVersions(&includeAllVersions) 
includeAuthoredContent := true
requestBody.SetIncludeAuthoredContent(&includeAuthoredContent) 
internalDueDateTime , err := time.Parse(time.RFC3339, "2022-07-20T22:42:28Z")
requestBody.SetInternalDueDateTime(&internalDueDateTime) 
dataSubject := graphmodels.NewDataSubject()
firstName := "Diego"
dataSubject.SetFirstName(&firstName) 
lastName := "Siciliani"
dataSubject.SetLastName(&lastName) 
email := "Diego.Siciliani@contoso.com"
dataSubject.SetEmail(&email) 
residency := "USA"
dataSubject.SetResidency(&residency) 
requestBody.SetDataSubject(dataSubject)
mailboxLocations := null
requestBody.SetMailboxLocations(&mailboxLocations) 
pauseAfterEstimate := true
requestBody.SetPauseAfterEstimate(&pauseAfterEstimate) 
regulations := []string {
	"CCPA",
}
requestBody.SetRegulations(regulations)
siteLocations := graphmodels.NewSubjectRightsRequestAllSiteLocation()
requestBody.SetSiteLocations(siteLocations)


user := graphmodels.NewUser()
id := "1B761ED2-AA7E-4D82-9CF5-C09D737B6167"
user.SetId(&id) 

approvers := []graphmodels.Userable {
	user,
}
requestBody.SetApprovers(approvers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
subjectRightsRequests, err := graphClient.Privacy().SubjectRightsRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SubjectRightsRequest subjectRightsRequest = new SubjectRightsRequest();
subjectRightsRequest.setType(SubjectRightsRequestType.Export);
subjectRightsRequest.setContentQuery("((\"Diego Siciliani\" OR \"Diego.Siciliani@contoso.com\") OR (participants:\"Diego.Siciliani@contoso.com\"))");
subjectRightsRequest.setDataSubjectType(DataSubjectType.Customer);
subjectRightsRequest.setExternalId("F53BF2DA-607D-412A-B568-FAA0F023AC0B");
subjectRightsRequest.setDisplayName("Export report for customer Id: 12345");
subjectRightsRequest.setDescription("This is a export request");
subjectRightsRequest.setIncludeAllVersions(false);
subjectRightsRequest.setIncludeAuthoredContent(true);
OffsetDateTime internalDueDateTime = OffsetDateTime.parse("2022-07-20T22:42:28Z");
subjectRightsRequest.setInternalDueDateTime(internalDueDateTime);
DataSubject dataSubject = new DataSubject();
dataSubject.setFirstName("Diego");
dataSubject.setLastName("Siciliani");
dataSubject.setEmail("Diego.Siciliani@contoso.com");
dataSubject.setResidency("USA");
subjectRightsRequest.setDataSubject(dataSubject);
subjectRightsRequest.setMailboxLocations(null);
subjectRightsRequest.setPauseAfterEstimate(true);
LinkedList<String> regulations = new LinkedList<String>();
regulations.add("CCPA");
subjectRightsRequest.setRegulations(regulations);
SubjectRightsRequestAllSiteLocation siteLocations = new SubjectRightsRequestAllSiteLocation();
siteLocations.setOdataType("microsoft.graph.subjectRightsRequestAllSiteLocation");
subjectRightsRequest.setSiteLocations(siteLocations);
LinkedList<User> approvers = new LinkedList<User>();
User user = new User();
user.setId("1B761ED2-AA7E-4D82-9CF5-C09D737B6167");
approvers.add(user);
subjectRightsRequest.setApprovers(approvers);
SubjectRightsRequest result = graphClient.privacy().subjectRightsRequests().post(subjectRightsRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const subjectRightsRequest = {
  type: 'export',
  contentQuery: '((\"Diego Siciliani\" OR \"Diego.Siciliani@contoso.com\") OR (participants:\"Diego.Siciliani@contoso.com\"))',
  dataSubjectType: 'customer',
  externalId: 'F53BF2DA-607D-412A-B568-FAA0F023AC0B',
  displayName: 'Export report for customer Id: 12345',
  description: 'This is a export request',
  includeAllVersions: false,
  includeAuthoredContent: true,
  internalDueDateTime: '2022-07-20T22:42:28Z',
  dataSubject: {
    firstName: 'Diego',
    lastName: 'Siciliani',
    email: 'Diego.Siciliani@contoso.com',
    residency: 'USA'
  },
  mailboxLocations: null,
  pauseAfterEstimate: true,
  regulations: [
    'CCPA'
  ],
  siteLocations: {
    '@odata.type': 'microsoft.graph.subjectRightsRequestAllSiteLocation'
  },
  approvers: [
    {
      id: '1B761ED2-AA7E-4D82-9CF5-C09D737B6167'
    }
  ]
};

await client.api('/privacy/subjectRightsRequests')
	.post(subjectRightsRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SubjectRightsRequest;
use Microsoft\Graph\Generated\Models\SubjectRightsRequestType;
use Microsoft\Graph\Generated\Models\DataSubjectType;
use Microsoft\Graph\Generated\Models\DataSubject;
use Microsoft\Graph\Generated\Models\SubjectRightsRequestAllSiteLocation;
use Microsoft\Graph\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SubjectRightsRequest();
$requestBody->setType(new SubjectRightsRequestType('export'));
$requestBody->setContentQuery('((\"Diego Siciliani\" OR \"Diego.Siciliani@contoso.com\") OR (participants:\"Diego.Siciliani@contoso.com\"))');
$requestBody->setDataSubjectType(new DataSubjectType('customer'));
$requestBody->setExternalId('F53BF2DA-607D-412A-B568-FAA0F023AC0B');
$requestBody->setDisplayName('Export report for customer Id: 12345');
$requestBody->setDescription('This is a export request');
$requestBody->setIncludeAllVersions(false);
$requestBody->setIncludeAuthoredContent(true);
$requestBody->setInternalDueDateTime(new \DateTime('2022-07-20T22:42:28Z'));
$dataSubject = new DataSubject();
$dataSubject->setFirstName('Diego');
$dataSubject->setLastName('Siciliani');
$dataSubject->setEmail('Diego.Siciliani@contoso.com');
$dataSubject->setResidency('USA');
$requestBody->setDataSubject($dataSubject);
$requestBody->setMailboxLocations(null);
$requestBody->setPauseAfterEstimate(true);
$requestBody->setRegulations(['CCPA', 	]);
$siteLocations = new SubjectRightsRequestAllSiteLocation();
$siteLocations->setOdataType('microsoft.graph.subjectRightsRequestAllSiteLocation');
$requestBody->setSiteLocations($siteLocations);
$approversUser1 = new User();
$approversUser1->setId('1B761ED2-AA7E-4D82-9CF5-C09D737B6167');
$approversArray []= $approversUser1;
$requestBody->setApprovers($approversArray);


$result = $graphServiceClient->privacy()->subjectRightsRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Compliance

$params = @{
	type = "export"
	contentQuery = "(("Diego Siciliani" OR "Diego.Siciliani@contoso.com") OR (participants:"Diego.Siciliani@contoso.com"))"
	dataSubjectType = "customer"
	externalId = "F53BF2DA-607D-412A-B568-FAA0F023AC0B"
	displayName = "Export report for customer Id: 12345"
	description = "This is a export request"
	includeAllVersions = $false
	includeAuthoredContent = $true
	internalDueDateTime = [System.DateTime]::Parse("2022-07-20T22:42:28Z")
	dataSubject = @{
		firstName = "Diego"
		lastName = "Siciliani"
		email = "Diego.Siciliani@contoso.com"
		residency = "USA"
	}
	mailboxLocations = $null
	pauseAfterEstimate = $true
	regulations = @(
	"CCPA"
)
siteLocations = @{
	"@odata.type" = "microsoft.graph.subjectRightsRequestAllSiteLocation"
}
approvers = @(
	@{
		id = "1B761ED2-AA7E-4D82-9CF5-C09D737B6167"
	}
)
}

New-MgPrivacySubjectRightsRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.subject_rights_request import SubjectRightsRequest
from msgraph.generated.models.subject_rights_request_type import SubjectRightsRequestType
from msgraph.generated.models.data_subject_type import DataSubjectType
from msgraph.generated.models.data_subject import DataSubject
from msgraph.generated.models.subject_rights_request_all_site_location import SubjectRightsRequestAllSiteLocation
from msgraph.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SubjectRightsRequest(
	type = SubjectRightsRequestType.Export,
	content_query = "((\"Diego Siciliani\" OR \"Diego.Siciliani@contoso.com\") OR (participants:\"Diego.Siciliani@contoso.com\"))",
	data_subject_type = DataSubjectType.Customer,
	external_id = "F53BF2DA-607D-412A-B568-FAA0F023AC0B",
	display_name = "Export report for customer Id: 12345",
	description = "This is a export request",
	include_all_versions = False,
	include_authored_content = True,
	internal_due_date_time = "2022-07-20T22:42:28Z",
	data_subject = DataSubject(
		first_name = "Diego",
		last_name = "Siciliani",
		email = "Diego.Siciliani@contoso.com",
		residency = "USA",
	),
	mailbox_locations = None,
	pause_after_estimate = True,
	regulations = [
		"CCPA",
	],
	site_locations = SubjectRightsRequestAllSiteLocation(
		odata_type = "microsoft.graph.subjectRightsRequestAllSiteLocation",
	),
	approvers = [
		User(
			id = "1B761ED2-AA7E-4D82-9CF5-C09D737B6167",
		),
	],
)

result = await graph_client.privacy.subject_rights_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "type": "export",
  "dataSubjectType": "customer",
  "regulations": [
    "CCPA"
  ],
  "displayName": "Export report for customer Id: 12345",
  "description": "This is a export request",
  "status": "active",
  "internalDueDateTime": "2022-07-20T22:42:28Z",
  "lastModifiedDateTime": "2022-05-10T22:42:28Z",
  "id": "CA084038-C5D2-493D-8DAB-23FC12393C76",
  "createdDateTime": "2022-05-10T22:42:28Z",
  "stages": [
    {
      "stage": "contentRetrieval",
      "status": "notStarted",
      "error": null
    },
    {
      "stage": "contentReview",
      "status": "notStarted",
      "error": null
    },
    {
      "stage": "generateReport",
      "status": "notStarted",
      "error": null
    },
    {
      "stage": "caseResolved",
      "status": "notStarted",
      "error": null
    }
  ],
  "createdBy": {
    "user": {
      "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167",
      "displayName": "srradmin@contoso.com"
    }
  },
  "approvers": [
    {
      "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167"
    }
  ],
  "collaborators": [
    {
      "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167"
    }
  ],
  "lastModifiedBy": {
    "user": {
      "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167",
      "displayName": "srradmin@contoso.com"
    }
  },
  "dataSubject": {
    "firstName": "Diego",
    "lastName": "Siciliani",
    "email": "Diego.Siciliani@contoso.com",
    "residency": "USA"
  },
  "team": {
    "id": "5484809c-fb5b-415a-afc6-da7ff601034e",
    "webUrl": "https://teams.contoso.com/teams/teamid"
  },
  "includeAllVersions": false,
  "pauseAfterEstimate": false,
  "includeAuthoredContent": false,
  "externalId": "F53BF2DA-607D-412A-B568-FAA0F023AC0B",
  "contentQuery": "((\"Diego Siciliani\" OR \"Diego.Siciliani@contoso.com\") OR (participants:\"Diego.Siciliani@contoso.com\"))",
  "mailboxLocations": null,
  "siteLocations": {
    "@odata.type": "microsoft.graph.subjectRightsRequestAllSiteLocation"
  }
}
```
