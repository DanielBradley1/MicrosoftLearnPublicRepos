<!-- Source: https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-legalholds?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# Create legalHold

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Create a new [legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All, eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | Not supported. |

## HTTP request

```http
POST /compliance/ediscovery/cases/{caseId}/legalHolds
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) object.

The following table lists the properties that are required when you create the [legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the legal hold. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.ediscovery.legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/compliance/ediscovery/cases/{caseId}/legalHolds
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.ediscovery.legalHold",
  "description": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "isEnabled": "Boolean",
  "status": "String",
  "contentQuery": "String",
  "errors": [
    "String"
  ],
  "displayName": "String"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Ediscovery;
using Microsoft.Graph.Beta.Models;

var requestBody = new LegalHold
{
	OdataType = "#microsoft.graph.ediscovery.legalHold",
	Description = "String",
	CreatedBy = new IdentitySet
	{
		OdataType = "microsoft.graph.identitySet",
	},
	IsEnabled = boolean,
	Status = LegalHoldStatus.Pending,
	ContentQuery = "String",
	Errors = new List<string>
	{
		"String",
	},
	DisplayName = "String",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Compliance.Ediscovery.Cases["{case-id}"].LegalHolds.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodelsediscovery "github.com/microsoftgraph/msgraph-beta-sdk-go/models/ediscovery"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodelsediscovery.NewLegalHold()
description := "String"
requestBody.SetDescription(&description) 
createdBy := graphmodels.NewIdentitySet()
requestBody.SetCreatedBy(createdBy)
isEnabled := boolean
requestBody.SetIsEnabled(&isEnabled) 
status := graphmodels.STRING_LEGALHOLDSTATUS 
requestBody.SetStatus(&status) 
contentQuery := "String"
requestBody.SetContentQuery(&contentQuery) 
errors := []string {
	"String",
}
requestBody.SetErrors(errors)
displayName := "String"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
legalHolds, err := graphClient.Compliance().Ediscovery().Cases().ByCaseId("case-id").LegalHolds().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.ediscovery.LegalHold legalHold = new com.microsoft.graph.beta.models.ediscovery.LegalHold();
legalHold.setOdataType("#microsoft.graph.ediscovery.legalHold");
legalHold.setDescription("String");
IdentitySet createdBy = new IdentitySet();
createdBy.setOdataType("microsoft.graph.identitySet");
legalHold.setCreatedBy(createdBy);
legalHold.setIsEnabled(boolean);
legalHold.setStatus(com.microsoft.graph.beta.models.ediscovery.LegalHoldStatus.Pending);
legalHold.setContentQuery("String");
LinkedList<String> errors = new LinkedList<String>();
errors.add("String");
legalHold.setErrors(errors);
legalHold.setDisplayName("String");
com.microsoft.graph.models.ediscovery.LegalHold result = graphClient.compliance().ediscovery().cases().byCaseId("{case-id}").legalHolds().post(legalHold);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const legalHold = {
  '@odata.type': '#microsoft.graph.ediscovery.legalHold',
  description: 'String',
  createdBy: {
    '@odata.type': 'microsoft.graph.identitySet'
  },
  isEnabled: 'Boolean',
  status: 'String',
  contentQuery: 'String',
  errors: [
    'String'
  ],
  displayName: 'String'
};

await client.api('/compliance/ediscovery/cases/{caseId}/legalHolds')
	.version('beta')
	.post(legalHold);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Ediscovery\LegalHold;
use Microsoft\Graph\Beta\Generated\Models\IdentitySet;
use Microsoft\Graph\Beta\Generated\Models\Ediscovery\LegalHoldStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LegalHold();
$requestBody->setOdataType('#microsoft.graph.ediscovery.legalHold');
$requestBody->setDescription('String');
$createdBy = new IdentitySet();
$createdBy->setOdataType('microsoft.graph.identitySet');
$requestBody->setCreatedBy($createdBy);
$requestBody->setIsEnabled(boolean);
$requestBody->setStatus(new LegalHoldStatus('string'));
$requestBody->setContentQuery('String');
$requestBody->setErrors(['String', 	]);
$requestBody->setDisplayName('String');

$result = $graphServiceClient->compliance()->ediscovery()->cases()->byCaseId('case-id')->legalHolds()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Compliance

$params = @{
	"@odata.type" = "#microsoft.graph.ediscovery.legalHold"
	description = "String"
	createdBy = @{
		"@odata.type" = "microsoft.graph.identitySet"
	}
	isEnabled = "Boolean"
	status = "String"
	contentQuery = "String"
	errors = @(
	"String"
)
displayName = "String"
}

New-MgBetaComplianceEdiscoveryCaseLegalHold -CaseId $caseId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.ediscovery.legal_hold import LegalHold
from msgraph_beta.generated.models.identity_set import IdentitySet
from msgraph_beta.generated.models.legal_hold_status import LegalHoldStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LegalHold(
	odata_type = "#microsoft.graph.ediscovery.legalHold",
	description = "String",
	created_by = IdentitySet(
		odata_type = "microsoft.graph.identitySet",
	),
	is_enabled = Boolean,
	status = LegalHoldStatus.Pending,
	content_query = "String",
	errors = [
		"String",
	],
	display_name = "String",
)

result = await graph_client.compliance.ediscovery.cases.by_case_id('case-id').legal_holds.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.ediscovery.legalHold",
  "id": "700cd868-d868-700c-68d8-0c7068d80c70",
  "description": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "isEnabled": "Boolean",
  "status": "String",
  "contentQuery": "String",
  "errors": [
    "String"
  ],
  "displayName": "String",
  "createdDateTime": "String (timestamp)"
}
```
