<!-- Source: https://learn.microsoft.com/en-us/graph/api/workforceintegration-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create workforceIntegration

Namespace: microsoft.graph

Create a new [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WorkforceIntegration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WorkforceIntegration.ReadWrite.All | Not available. |

> **Note**: This API supports admin permissions. Users with admin roles can access groups that they are not a member of.

## HTTP request

```http
POST /teamwork/workforceIntegrations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply a JSON representation of the [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0) object.

The following table lists the properties that you can use when you create a **workforceIntegration** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| apiVersion | Int32 | API version for the callback URL. Start with 1. |
| displayName | String | Name of the workforce integration. |
| eligibilityFilteringEnabledEntities | eligibilityFilteringEnabledEntities | Support to view eligibility-filtered results. The possible values are: `none`, `swapRequest`, `offerShiftRequest`, `unknownFutureValue`, `timeOffReason`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `timeOffReason`. |
| encryption | [workforceIntegrationEncryption](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegrationencryption?view=graph-rest-1.0) | The workforce integration encryption resource. |
| isActive | Boolean | Indicates whether this workforce integration is currently active and available. |
| supportedEntities | workforceIntegrationSupportedEntities | The Shifts entities supported for synchronous change notifications. Shifts call the provided URL when client changes occur to the entities specified in this property. By default, no entities are supported for change notifications. The possible values are: `none`, `shift`, `swapRequest`, `userShiftPreferences`, `openShift`, `openShiftRequest`, `offerShiftRequest`, `unknownFutureValue`, `timeCard`, `timeOffReason`, `timeOff`, `timeOffRequest`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `timeCard`, `timeOffReason` , `timeOff` , `timeOffRequest`. |
| url | String | Workforce integration URL used for callbacks from the Shifts service. |

## Response

If successful, this method returns a `201 Created` response code and a new [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/teamwork/workforceIntegrations
Content-Type: application/json

{
  "displayName": "ABCWorkforceIntegration",
  "apiVersion": 1,
  "isActive": true,
  "encryption": {
    "protocol": "sharedSecret",
    "secret": "My Secret"
  },
  "url": "https://ABCWorkforceIntegration.com/Contoso/",
  "supportedEntities": "Shift,SwapRequest",
  "eligibilityFilteringEnabledEntities": "SwapRequest"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new WorkforceIntegration
{
	DisplayName = "ABCWorkforceIntegration",
	ApiVersion = 1,
	IsActive = true,
	Encryption = new WorkforceIntegrationEncryption
	{
		Protocol = WorkforceIntegrationEncryptionProtocol.SharedSecret,
		Secret = "My Secret",
	},
	Url = "https://ABCWorkforceIntegration.com/Contoso/",
	SupportedEntities = WorkforceIntegrationSupportedEntities.Shift | WorkforceIntegrationSupportedEntities.SwapRequest,
	EligibilityFilteringEnabledEntities = EligibilityFilteringEnabledEntities.SwapRequest,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teamwork.WorkforceIntegrations.PostAsync(requestBody);
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

requestBody := graphmodels.NewWorkforceIntegration()
displayName := "ABCWorkforceIntegration"
requestBody.SetDisplayName(&displayName) 
apiVersion := int32(1)
requestBody.SetApiVersion(&apiVersion) 
isActive := true
requestBody.SetIsActive(&isActive) 
encryption := graphmodels.NewWorkforceIntegrationEncryption()
protocol := graphmodels.SHAREDSECRET_WORKFORCEINTEGRATIONENCRYPTIONPROTOCOL 
encryption.SetProtocol(&protocol) 
secret := "My Secret"
encryption.SetSecret(&secret) 
requestBody.SetEncryption(encryption)
url := "https://ABCWorkforceIntegration.com/Contoso/"
requestBody.SetUrl(&url) 
supportedEntities := graphmodels.SHIFT,SWAPREQUEST_WORKFORCEINTEGRATIONSUPPORTEDENTITIES 
requestBody.SetSupportedEntities(&supportedEntities) 
eligibilityFilteringEnabledEntities := graphmodels.SWAPREQUEST_ELIGIBILITYFILTERINGENABLEDENTITIES 
requestBody.SetEligibilityFilteringEnabledEntities(&eligibilityFilteringEnabledEntities) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
workforceIntegrations, err := graphClient.Teamwork().WorkforceIntegrations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WorkforceIntegration workforceIntegration = new WorkforceIntegration();
workforceIntegration.setDisplayName("ABCWorkforceIntegration");
workforceIntegration.setApiVersion(1);
workforceIntegration.setIsActive(true);
WorkforceIntegrationEncryption encryption = new WorkforceIntegrationEncryption();
encryption.setProtocol(WorkforceIntegrationEncryptionProtocol.SharedSecret);
encryption.setSecret("My Secret");
workforceIntegration.setEncryption(encryption);
workforceIntegration.setUrl("https://ABCWorkforceIntegration.com/Contoso/");
workforceIntegration.setSupportedEntities(EnumSet.of(WorkforceIntegrationSupportedEntities.Shift, WorkforceIntegrationSupportedEntities.SwapRequest));
workforceIntegration.setEligibilityFilteringEnabledEntities(EnumSet.of(EligibilityFilteringEnabledEntities.SwapRequest));
WorkforceIntegration result = graphClient.teamwork().workforceIntegrations().post(workforceIntegration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workforceIntegration = {
  displayName: 'ABCWorkforceIntegration',
  apiVersion: 1,
  isActive: true,
  encryption: {
    protocol: 'sharedSecret',
    secret: 'My Secret'
  },
  url: 'https://ABCWorkforceIntegration.com/Contoso/',
  supportedEntities: 'Shift,SwapRequest',
  eligibilityFilteringEnabledEntities: 'SwapRequest'
};

await client.api('/teamwork/workforceIntegrations')
	.post(workforceIntegration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\WorkforceIntegration;
use Microsoft\Graph\Generated\Models\WorkforceIntegrationEncryption;
use Microsoft\Graph\Generated\Models\WorkforceIntegrationEncryptionProtocol;
use Microsoft\Graph\Generated\Models\WorkforceIntegrationSupportedEntities;
use Microsoft\Graph\Generated\Models\EligibilityFilteringEnabledEntities;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WorkforceIntegration();
$requestBody->setDisplayName('ABCWorkforceIntegration');
$requestBody->setApiVersion(1);
$requestBody->setIsActive(true);
$encryption = new WorkforceIntegrationEncryption();
$encryption->setProtocol(new WorkforceIntegrationEncryptionProtocol('sharedSecret'));
$encryption->setSecret('My Secret');
$requestBody->setEncryption($encryption);
$requestBody->setUrl('https://ABCWorkforceIntegration.com/Contoso/');
$requestBody->setSupportedEntities(new WorkforceIntegrationSupportedEntities('shift,SwapRequest'));
$requestBody->setEligibilityFilteringEnabledEntities(new EligibilityFilteringEnabledEntities('swapRequest'));

$result = $graphServiceClient->teamwork()->workforceIntegrations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	displayName = "ABCWorkforceIntegration"
	apiVersion = 1
	isActive = $true
	encryption = @{
		protocol = "sharedSecret"
		secret = "My Secret"
	}
	url = "https://ABCWorkforceIntegration.com/Contoso/"
	supportedEntities = "Shift,SwapRequest"
	eligibilityFilteringEnabledEntities = "SwapRequest"
}

New-MgTeamworkWorkforceIntegration -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.workforce_integration import WorkforceIntegration
from msgraph.generated.models.workforce_integration_encryption import WorkforceIntegrationEncryption
from msgraph.generated.models.workforce_integration_encryption_protocol import WorkforceIntegrationEncryptionProtocol
from msgraph.generated.models.workforce_integration_supported_entities import WorkforceIntegrationSupportedEntities
from msgraph.generated.models.eligibility_filtering_enabled_entities import EligibilityFilteringEnabledEntities
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WorkforceIntegration(
	display_name = "ABCWorkforceIntegration",
	api_version = 1,
	is_active = True,
	encryption = WorkforceIntegrationEncryption(
		protocol = WorkforceIntegrationEncryptionProtocol.SharedSecret,
		secret = "My Secret",
	),
	url = "https://ABCWorkforceIntegration.com/Contoso/",
	supported_entities = WorkforceIntegrationSupportedEntities.Shift | WorkforceIntegrationSupportedEntities.SwapRequest,
	eligibility_filtering_enabled_entities = EligibilityFilteringEnabledEntities.SwapRequest,
)

result = await graph_client.teamwork.workforce_integrations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "c5d0c76b-80c4-481c-be50-923cd8d680a1",
  "displayName": "ABCWorkforceIntegration",
  "apiVersion": 1,
  "isActive": true,
  "encryption": {
    "protocol": "sharedSecret",
    "secret": null
  },
  "url": "https://abcWorkforceIntegration.com/Contoso/",
  "supportedEntities": "Shift,SwapRequest",
  "eligibilityFilteringEnabledEntities": "SwapRequest"
}
```

## Examples for use cases of WorkforceIntegration entity for Eligibility Filtering by workforce management system \(WFM\) rules

### Use case: Create a new WorkforceIntegration with SwapRequest enabled for eligibility filtering

### Request

The following example shows a request.

```
POST https://graph.microsoft.com/v1.0/teamwork/workforceIntegrations/
Authorization: Bearer {token}
Content-type: application/json

{
  "displayName": "ABCWorkforceIntegration",
  "apiVersion": 1,
  "isActive": true,
  "encryption": {
    "protocol": "sharedSecret",
    "secret": "My Secret"
  },
  "url": "https://ABCWorkforceIntegration.com/Contoso/",
  "supportedEntities": "Shift,SwapRequest",
  "eligibilityFilteringEnabledEntities": "SwapRequest"
}
```

### Response

The following example shows the response.

```
HTTP/1.1 200 OK
{
  "id": "c5d0c76b-80c4-481c-be50-923cd8d680a1",
  "displayName": "ABCWorkforceIntegration",
  "apiVersion": 1,
  "isActive": true,
  "encryption": {
    "protocol": "sharedSecret",
    "secret": null
  },
  "url": "https://abcWorkforceIntegration.com/Contoso/",
  "supportedEntities": "Shift,SwapRequest",
  "eligibilityFilteringEnabledEntities": "SwapRequest"
}
```

To see how to update an existing workforceIntegration with SwapRequest enabled for eligibility filtering, see [Update](https://learn.microsoft.com/en-us/graph/api/workforceintegration-update?view=graph-rest-1.0).

## Example of fetching eligible shifts when SwapRequest is included in eligibilityFilteringEnabledEntities

The interaction between Shifts app and workforce integration endpoints follow the existing pattern.

### Request

This example shows a request made by Shifts to the workforce integration endpoint to fetch eligible shifts for a swap request.

```
POST https://abcWorkforceIntegration.com/Contoso/{apiVersion}/team/{teamId}/read
Accept-Language: en-us
{
  "requests": [
  {
     "id": "{shiftId}",
     "method": "GET”,
     "url": “/shifts/{shiftId}/requestableShifts?requestType={requestType}&startDateTime={startDateTime}&endDateTime={endDateTime}”
   }]
}
```

### Response

The following example shows the response from the workforce integration service.

```
HTTP/1.1 200 OK
{
  "responses": [
    "id": "{shiftId}",
    "status: 200,
    "body": {
       "data": [{shiftId}, {shiftId}...]
       "error": null
    }
  ]
}
```
