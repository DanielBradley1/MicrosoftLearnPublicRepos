<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-yeartimeperioddefinition-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create yearTimePeriodDefinition

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-TimePeriod.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IndustryData-TimePeriod.ReadWrite.All | Not available. |

## HTTP request

```http
POST /external/industryData/years
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.industryData.yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) object.

You can specify the following properties when you create a **yearTimePeriodDefinition**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the year. Maximum supported length is 100 characters. Required. |
| endDate | Date | The last day of the year using ISO 8601 format for date. Required. |
| startDate | Date | The first day of the year using ISO 8601 format for date. Required. |
| year | [microsoft.graph.industryData.yearReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yearreferencevalue?view=graph-rest-beta) | A pointer to a year entry in the [referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) collection. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.industryData.yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/external/industryData/years
Content-Type: application/json
Content-length: 242

{
  "displayName": "Fiscal Year 2022",
  "endDate": "2023-06-15",
  "startDate": "2022-09-01",
  "year": {
    "code": "2022"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new YearTimePeriodDefinition
{
	DisplayName = "Fiscal Year 2022",
	EndDate = new Date(DateTime.Parse("2023-06-15")),
	StartDate = new Date(DateTime.Parse("2022-09-01")),
	Year = new YearReferenceValue
	{
		Code = "2022",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.Years.PostAsync(requestBody);
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

requestBody := graphmodelsindustrydata.NewYearTimePeriodDefinition()
displayName := "Fiscal Year 2022"
requestBody.SetDisplayName(&displayName) 
endDate := 2023-06-15
requestBody.SetEndDate(&endDate) 
startDate := 2022-09-01
requestBody.SetStartDate(&startDate) 
year := graphmodelsindustrydata.NewYearReferenceValue()
code := "2022"
year.SetCode(&code) 
requestBody.SetYear(year)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
years, err := graphClient.External().IndustryData().Years().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.YearTimePeriodDefinition yearTimePeriodDefinition = new com.microsoft.graph.beta.models.industrydata.YearTimePeriodDefinition();
yearTimePeriodDefinition.setDisplayName("Fiscal Year 2022");
LocalDate endDate = LocalDate.parse("2023-06-15");
yearTimePeriodDefinition.setEndDate(endDate);
LocalDate startDate = LocalDate.parse("2022-09-01");
yearTimePeriodDefinition.setStartDate(startDate);
com.microsoft.graph.beta.models.industrydata.YearReferenceValue year = new com.microsoft.graph.beta.models.industrydata.YearReferenceValue();
year.setCode("2022");
yearTimePeriodDefinition.setYear(year);
com.microsoft.graph.models.industrydata.YearTimePeriodDefinition result = graphClient.external().industryData().years().post(yearTimePeriodDefinition);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const yearTimePeriodDefinition = {
  displayName: 'Fiscal Year 2022',
  endDate: '2023-06-15',
  startDate: '2022-09-01',
  year: {
    code: '2022'
  }
};

await client.api('/external/industryData/years')
	.version('beta')
	.post(yearTimePeriodDefinition);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\YearTimePeriodDefinition;
use Microsoft\Kiota\Abstractions\Types\Date;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\YearReferenceValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new YearTimePeriodDefinition();
$requestBody->setDisplayName('Fiscal Year 2022');
$requestBody->setEndDate(new Date('2023-06-15'));
$requestBody->setStartDate(new Date('2022-09-01'));
$year = new YearReferenceValue();
$year->setCode('2022');
$requestBody->setYear($year);

$result = $graphServiceClient->external()->industryData()->years()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	displayName = "Fiscal Year 2022"
	endDate = "2023-06-15"
	startDate = "2022-09-01"
	year = @{
		code = "2022"
	}
}

New-MgBetaExternalIndustryDataYear -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.year_time_period_definition import YearTimePeriodDefinition
from msgraph_beta.generated.models.industry_data.year_reference_value import YearReferenceValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = YearTimePeriodDefinition(
	display_name = "Fiscal Year 2022",
	end_date = "2023-06-15",
	start_date = "2022-09-01",
	year = YearReferenceValue(
		code = "2022",
	),
)

result = await graph_client.external.industry_data.years.post(request_body)
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/years/$entity",
  "displayName": "Fiscal Year 2022",
  "endDate": "2023-06-15",
  "id": "ebf18762-ab92-487e-21d1-08daddab28bb",
  "startDate": "2022-09-01",
  "year": {
    "code": "2022"
  }
}
```
