<!-- Source: https://learn.microsoft.com/en-us/graph/api/subjectrightsrequest-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update subjectRightsRequest

Namespace: microsoft.graph

Update the properties of a [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0) object.

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
PATCH /security/subjectRightsRequests/{subjectRightsRequestId}
PATCH /privacy/subjectRightsRequests/{subjectRightsRequestId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0) object.

The following table shows the properties that are required when you update the [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | [microsoft.graph.identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The identity information for the user that the request is assigned to. |
| description | String | Updated description for the request. |
| displayName | String | Updated name of the request. |
| internalDueDateTime | DateTimeOffset | Updated internal due date for the request. |

## Response

If successful, this method returns a `200 OK` response code and an updated [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/privacy/subjectRightsRequests/{subjectRightsRequestId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.subjectRightsRequest",
  "internalDueDateTime": "2021-08-30T00:00:00Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SubjectRightsRequest
{
	OdataType = "#microsoft.graph.subjectRightsRequest",
	InternalDueDateTime = DateTimeOffset.Parse("2021-08-30T00:00:00Z"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Privacy.SubjectRightsRequests["{subjectRightsRequest-id}"].PatchAsync(requestBody);
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
internalDueDateTime , err := time.Parse(time.RFC3339, "2021-08-30T00:00:00Z")
requestBody.SetInternalDueDateTime(&internalDueDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
subjectRightsRequests, err := graphClient.Privacy().SubjectRightsRequests().BySubjectRightsRequestId("subjectRightsRequest-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SubjectRightsRequest subjectRightsRequest = new SubjectRightsRequest();
subjectRightsRequest.setOdataType("#microsoft.graph.subjectRightsRequest");
OffsetDateTime internalDueDateTime = OffsetDateTime.parse("2021-08-30T00:00:00Z");
subjectRightsRequest.setInternalDueDateTime(internalDueDateTime);
SubjectRightsRequest result = graphClient.privacy().subjectRightsRequests().bySubjectRightsRequestId("{subjectRightsRequest-id}").patch(subjectRightsRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const subjectRightsRequest = {
  '@odata.type': '#microsoft.graph.subjectRightsRequest',
  internalDueDateTime: '2021-08-30T00:00:00Z'
};

await client.api('/privacy/subjectRightsRequests/{subjectRightsRequestId}')
	.update(subjectRightsRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SubjectRightsRequest;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SubjectRightsRequest();
$requestBody->setOdataType('#microsoft.graph.subjectRightsRequest');
$requestBody->setInternalDueDateTime(new \DateTime('2021-08-30T00:00:00Z'));

$result = $graphServiceClient->privacy()->subjectRightsRequests()->bySubjectRightsRequestId('subjectRightsRequest-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Compliance

$params = @{
	"@odata.type" = "#microsoft.graph.subjectRightsRequest"
	internalDueDateTime = [System.DateTime]::Parse("2021-08-30T00:00:00Z")
}

Update-MgPrivacySubjectRightsRequest -SubjectRightsRequestId $subjectRightsRequestId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.subject_rights_request import SubjectRightsRequest
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SubjectRightsRequest(
	odata_type = "#microsoft.graph.subjectRightsRequest",
	internal_due_date_time = "2021-08-30T00:00:00Z",
)

result = await graph_client.privacy.subject_rights_requests.by_subject_rights_request_id('subjectRightsRequest-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "displayName": "Updated case name for Diego Siciliani",
  "description": "This is an updated case",
  "internalDueDateTime": "2022-07-20T22:42:28Z"
}
```
