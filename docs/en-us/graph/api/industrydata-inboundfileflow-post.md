<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-inboundfileflow-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-05 -->

# Create inboundFileFlow

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [inboundFileFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundfileflow?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-InboundFlow.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IndustryData-InboundFlow.ReadWrite.All | Not available. |

## HTTP request

```http
POST /external/industryData/inboundFlows
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [inboundFileFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundfileflow?view=graph-rest-beta) object.

The following table lists the required and optional properties for creating an **inboundFileFlow** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| dataDomain | microsoft.graph.industryData.inboundDomain | The category of data that is being imported in this flow. The possible values are: `educationRostering`, `unknownFutureValue`. Required. |
| displayName | String | The name of the process. Inherited from [industryDataActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivity?view=graph-rest-beta). Required. |
| effectiveDateTime | DateTimeOffset | The start of the time window when the flow is allowed to run. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Required. |
| expirationDateTime | DateTimeOffset | The end of the time window when the flow is allowed to run. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Optional. |
| dataConnector | [microsoft.graph.industryData.industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) | The data connector to the source system from where this flow gets its data. Inherited from [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta). |
| year | [microsoft.graph.industryData.yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) | The year associated to the data that this flow brings in. Inherited from [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta). |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.industryData.inboundFileFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundfileflow?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/external/industryData/inboundFlows
Content-Type: application/json
Content-length: 246

{
  "@odata.type": "#microsoft.graph.industryData.inboundFileFlow",
  "dataConnector@odata.bind": "https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271",
  "dataDomain": "educationRostering",
  "displayName": "Inbound rostering flow",
  "effectiveDateTime": "2023-03-12T16:40:46.924769+05:30",
  "expirationDateTime": "2023-03-13T16:40:46.924769+05:30",
  "year@odata.bind": "https://graph.microsoft.com/beta/external/industryData/years/ebf18762-ab92-487e-21d1-08daddab28bb"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new InboundFileFlow
{
	OdataType = "#microsoft.graph.industryData.inboundFileFlow",
	DataDomain = InboundDomain.EducationRostering,
	DisplayName = "Inbound rostering flow",
	EffectiveDateTime = DateTimeOffset.Parse("2023-03-12T16:40:46.924769+05:30"),
	ExpirationDateTime = DateTimeOffset.Parse("2023-03-13T16:40:46.924769+05:30"),
	AdditionalData = new Dictionary<string, object>
	{
		{
			"dataConnector@odata.bind" , "https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271"
		},
		{
			"year@odata.bind" , "https://graph.microsoft.com/beta/external/industryData/years/ebf18762-ab92-487e-21d1-08daddab28bb"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.InboundFlows.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodelsindustrydata "github.com/microsoftgraph/msgraph-beta-sdk-go/models/industrydata"
	  //other-imports
)

requestBody := graphmodelsindustrydata.NewInboundFlow()
dataDomain := graphmodels.EDUCATIONROSTERING_INBOUNDDOMAIN 
requestBody.SetDataDomain(&dataDomain) 
displayName := "Inbound rostering flow"
requestBody.SetDisplayName(&displayName) 
effectiveDateTime , err := time.Parse(time.RFC3339, "2023-03-12T16:40:46.924769+05:30")
requestBody.SetEffectiveDateTime(&effectiveDateTime) 
expirationDateTime , err := time.Parse(time.RFC3339, "2023-03-13T16:40:46.924769+05:30")
requestBody.SetExpirationDateTime(&expirationDateTime) 
additionalData := map[string]interface{}{
	"dataConnector@odata.bind" : "https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271", 
	"year@odata.bind" : "https://graph.microsoft.com/beta/external/industryData/years/ebf18762-ab92-487e-21d1-08daddab28bb", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
inboundFlows, err := graphClient.External().IndustryData().InboundFlows().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.InboundFileFlow inboundFlow = new com.microsoft.graph.beta.models.industrydata.InboundFileFlow();
inboundFlow.setOdataType("#microsoft.graph.industryData.inboundFileFlow");
inboundFlow.setDataDomain(com.microsoft.graph.beta.models.industrydata.InboundDomain.EducationRostering);
inboundFlow.setDisplayName("Inbound rostering flow");
OffsetDateTime effectiveDateTime = OffsetDateTime.parse("2023-03-12T16:40:46.924769+05:30");
inboundFlow.setEffectiveDateTime(effectiveDateTime);
OffsetDateTime expirationDateTime = OffsetDateTime.parse("2023-03-13T16:40:46.924769+05:30");
inboundFlow.setExpirationDateTime(expirationDateTime);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("dataConnector@odata.bind", "https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271");
additionalData.put("year@odata.bind", "https://graph.microsoft.com/beta/external/industryData/years/ebf18762-ab92-487e-21d1-08daddab28bb");
inboundFlow.setAdditionalData(additionalData);
com.microsoft.graph.models.industrydata.InboundFlow result = graphClient.external().industryData().inboundFlows().post(inboundFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const inboundFlow = {
  '@odata.type': '#microsoft.graph.industryData.inboundFileFlow',
  'dataConnector@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271',
  dataDomain: 'educationRostering',
  displayName: 'Inbound rostering flow',
  effectiveDateTime: '2023-03-12T16:40:46.924769+05:30',
  expirationDateTime: '2023-03-13T16:40:46.924769+05:30',
  'year@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/years/ebf18762-ab92-487e-21d1-08daddab28bb'
};

await client.api('/external/industryData/inboundFlows')
	.version('beta')
	.post(inboundFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\InboundFileFlow;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\InboundDomain;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new InboundFileFlow();
$requestBody->setOdataType('#microsoft.graph.industryData.inboundFileFlow');
$requestBody->setDataDomain(new InboundDomain('educationRostering'));
$requestBody->setDisplayName('Inbound rostering flow');
$requestBody->setEffectiveDateTime(new \DateTime('2023-03-12T16:40:46.924769+05:30'));
$requestBody->setExpirationDateTime(new \DateTime('2023-03-13T16:40:46.924769+05:30'));
$additionalData = [
	'dataConnector@odata.bind' => 'https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271',
	'year@odata.bind' => 'https://graph.microsoft.com/beta/external/industryData/years/ebf18762-ab92-487e-21d1-08daddab28bb',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->external()->industryData()->inboundFlows()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "#microsoft.graph.industryData.inboundFileFlow"
	"dataConnector@odata.bind" = "https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271"
	dataDomain = "educationRostering"
	displayName = "Inbound rostering flow"
	effectiveDateTime = [System.DateTime]::Parse("2023-03-12T16:40:46.924769+05:30")
	expirationDateTime = [System.DateTime]::Parse("2023-03-13T16:40:46.924769+05:30")
	"year@odata.bind" = "https://graph.microsoft.com/beta/external/industryData/years/ebf18762-ab92-487e-21d1-08daddab28bb"
}

New-MgBetaExternalIndustryDataInboundFlow -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.inbound_file_flow import InboundFileFlow
from msgraph_beta.generated.models.inbound_domain import InboundDomain
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = InboundFileFlow(
	odata_type = "#microsoft.graph.industryData.inboundFileFlow",
	data_domain = InboundDomain.EducationRostering,
	display_name = "Inbound rostering flow",
	effective_date_time = "2023-03-12T16:40:46.924769+05:30",
	expiration_date_time = "2023-03-13T16:40:46.924769+05:30",
	additional_data = {
			"data_connector@odata_bind" : "https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271",
			"year@odata_bind" : "https://graph.microsoft.com/beta/external/industryData/years/ebf18762-ab92-487e-21d1-08daddab28bb",
	}
)

result = await graph_client.external.industry_data.inbound_flows.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.industryData.inboundFileFlow",
  "dataDomain": "educationRostering",
  "displayName": "Inbound rostering fow",
  "effectiveDateTime": "2023-03-12T11:10:46.924769Z",
  "expirationDateTime": "2023-03-13T11:10:46.924769Z",
  "id": "7bd62d17-8c37-4494-f68d-08daddab2911",
  "readinessStatus": "ready"
}
```
