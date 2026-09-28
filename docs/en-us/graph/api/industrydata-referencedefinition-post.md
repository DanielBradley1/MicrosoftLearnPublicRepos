<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-referencedefinition-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-28 -->

# Create referenceDefinition

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) object.

**referenceDefinition** objects associate incoming data with standardized reference types values for validation.

You can extend the following reference types with other codes that better align with your source data.

| Name | ReferenceType |
| :--- | :--- |
| Academic Subjects | RefAcademicSubject |
| Demographic: Race | RefRace |
| Demographic: Ethnicity | RefEthnicity |
| Grade Level | RefGradeLevel |
| Organization Types | RefOrgType |
| Person Flags | RefPersonFlagType |

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-ReferenceDefinition.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IndustryData-ReferenceDefinition.ReadWrite.All | Not available. |

## HTTP request

```http
POST /external/industryData/referenceDefinitions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) object.

The following table lists the required and optional properties for creating a **referenceDefinition** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| referenceType | String | The categorical type for a collection enumerated values. Required. |
| displayName | String | A human-readable representation of the reference code value for display in a user interface. Optional. |
| code | String | Code value for the definition. Must be unique within the referenceType. Required. |
| isDisabled | Boolean | Indicates whether the definition is disabled. Required. |
| sortIndex | Int32 | The index that specifies the order in which to present the definition to the user. Must be unique within the referenceType. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.industryData.referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/external/industryData/referenceDefinitions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.industryData.referenceDefinition",
  "referenceType": "RefGradeLevel",
  "code": "TestGrade",
  "isDisabled": false,
  "sortIndex": 300,
  "displayName": "New Test Grade Level"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new ReferenceDefinition
{
	OdataType = "#microsoft.graph.industryData.referenceDefinition",
	ReferenceType = "RefGradeLevel",
	Code = "TestGrade",
	IsDisabled = false,
	SortIndex = 300,
	DisplayName = "New Test Grade Level",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.ReferenceDefinitions.PostAsync(requestBody);
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
	  graphmodelsindustrydata "github.com/microsoftgraph/msgraph-beta-sdk-go/models/industrydata"
	  //other-imports
)

requestBody := graphmodelsindustrydata.NewReferenceDefinition()
referenceType := "RefGradeLevel"
requestBody.SetReferenceType(&referenceType) 
code := "TestGrade"
requestBody.SetCode(&code) 
isDisabled := false
requestBody.SetIsDisabled(&isDisabled) 
sortIndex := int32(300)
requestBody.SetSortIndex(&sortIndex) 
displayName := "New Test Grade Level"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
referenceDefinitions, err := graphClient.External().IndustryData().ReferenceDefinitions().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.ReferenceDefinition referenceDefinition = new com.microsoft.graph.beta.models.industrydata.ReferenceDefinition();
referenceDefinition.setOdataType("#microsoft.graph.industryData.referenceDefinition");
referenceDefinition.setReferenceType("RefGradeLevel");
referenceDefinition.setCode("TestGrade");
referenceDefinition.setIsDisabled(false);
referenceDefinition.setSortIndex(300);
referenceDefinition.setDisplayName("New Test Grade Level");
com.microsoft.graph.models.industrydata.ReferenceDefinition result = graphClient.external().industryData().referenceDefinitions().post(referenceDefinition);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const referenceDefinition = {
  '@odata.type': '#microsoft.graph.industryData.referenceDefinition',
  referenceType: 'RefGradeLevel',
  code: 'TestGrade',
  isDisabled: false,
  sortIndex: 300,
  displayName: 'New Test Grade Level'
};

await client.api('/external/industryData/referenceDefinitions')
	.version('beta')
	.post(referenceDefinition);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\ReferenceDefinition;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReferenceDefinition();
$requestBody->setOdataType('#microsoft.graph.industryData.referenceDefinition');
$requestBody->setReferenceType('RefGradeLevel');
$requestBody->setCode('TestGrade');
$requestBody->setIsDisabled(false);
$requestBody->setSortIndex(300);
$requestBody->setDisplayName('New Test Grade Level');

$result = $graphServiceClient->external()->industryData()->referenceDefinitions()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "#microsoft.graph.industryData.referenceDefinition"
	referenceType = "RefGradeLevel"
	code = "TestGrade"
	isDisabled = $false
	sortIndex = 300
	displayName = "New Test Grade Level"
}

New-MgBetaExternalIndustryDataReferenceDefinition -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.reference_definition import ReferenceDefinition
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReferenceDefinition(
	odata_type = "#microsoft.graph.industryData.referenceDefinition",
	reference_type = "RefGradeLevel",
	code = "TestGrade",
	is_disabled = False,
	sort_index = 300,
	display_name = "New Test Grade Level",
)

result = await graph_client.external.industry_data.reference_definitions.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.industryData.referenceDefinition",
  "id": "RefGradeLevel-TestGrade",
  "referenceType": "RefGradeLevel",
  "displayName": "New Test Grade Level",
  "code": "TestGrade",
  "source": "Tenant Defined",
  "isDisabled": false,
  "sortIndex": 300,
  "createdDateTime": "2024-03-13T18:20:26.3796502Z",
  "lastModifiedDateTime": "2024-03-13T18:20:26.3796502Z"
}
```
